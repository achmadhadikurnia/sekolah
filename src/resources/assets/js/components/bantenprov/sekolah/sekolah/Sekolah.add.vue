<template>
  <div class="card">
    <div class="card-header">
      <i class="fa fa-table" aria-hidden="true"></i> {{ title }}

      <ul class="nav nav-pills card-header-pills pull-right">
        <li class="nav-item">
          <button class="btn btn-default btn-sm" role="button" @click="back">
            <i class="fa fa-arrow-left" aria-hidden="true"></i>
          </button>
        </li>
      </ul>
    </div>

    <div class="card-body">
      <vue-form class="form-horizontal form-validation" :state="state" @submit.prevent="onSubmit">
        <div class="form-row">
          <div class="col-md">
            <validate tag="div">
              <label for="nama">Nama Sekolah</label>
              <input type="text" class="form-control" name="nama" v-model="model.nama" placeholder="Nama Sekolah" required autofocus>

              <field-messages name="nama" show="$invalid && $submitted" class="text-danger">
                <small class="form-text text-success">Looks good!</small>
                <small class="form-text text-danger" slot="required">Nama Sekolah UN is a required field</small>
              </field-messages>
            </validate>
          </div>
        </div>

        <div class="form-row mt-4">
          <div class="col-md">
            <validate tag="div">
              <label for="npsn">NPSN</label>
              <input type="number" class="form-control" name="npsn" v-model="model.npsn" placeholder="NPSN" required>

              <field-messages name="npsn" show="$invalid && $submitted" class="text-danger">
                <small class="form-text text-success">Looks good!</small>
                <small class="form-text text-danger" slot="required">NPSN is a required field</small>
              </field-messages>
            </validate>
          </div>
        </div>

        <div class="form-row mt-4">
          <div class="col-md">
            <validate tag="div">
              <label for="jenis_sekolah_id">Jenis Sekolah</label>
              <v-select name="jenis_sekolah_id" v-model="model.jenis_sekolah" :options="jenis_sekolah" placeholder="Jenis Sekolah" required></v-select>

              <field-messages name="jenis_sekolah_id" show="$invalid && $submitted" class="text-danger">
                <small class="form-text text-success">Looks good!</small>
                <small class="form-text text-danger" slot="required">Jenis Sekolah is a required field</small>
              </field-messages>
            </validate>
          </div>
        </div>

        <div class="form-row mt-4">
          <div class="col-md">
            <validate tag="div">
              <label for="alamat">Alamat</label>
              <input type="text" class="form-control" name="alamat" v-model="model.alamat" placeholder="Alamat" required>

              <field-messages name="alamat" show="$invalid && $submitted" class="text-danger">
                <small class="form-text text-success">Looks good!</small>
                <small class="form-text text-danger" slot="required">Alamat is a required field</small>
              </field-messages>
            </validate>
          </div>
        </div>

        <!-- <div class="form-row mt-4">
          <div class="col-md">
            <validate tag="div">
              <label for="logo">Logo</label>
              <input type="text" class="form-control" name="logo" v-model="model.logo" placeholder="Logo" required>

              <field-messages name="logo" show="$invalid && $submitted" class="text-danger">
                <small class="form-text text-success">Looks good!</small>
                <small class="form-text text-danger" slot="required">Logo is a required field</small>
              </field-messages>
            </validate>
          </div>
        </div> -->

        <!-- <div class="form-row mt-4">
          <div class="col-md">
            <validate tag="div">
              <label for="foto_gedung">Foto Gedung</label>
              <input type="text" class="form-control" name="foto_gedung" v-model="model.foto_gedung" placeholder="Foto Gedung" required>

              <field-messages name="foto_gedung" show="$invalid && $submitted" class="text-danger">
                <small class="form-text text-success">Looks good!</small>
                <small class="form-text text-danger" slot="required">Foto Gedung is a required field</small>
              </field-messages>
            </validate>
          </div>
        </div> -->

        <div class="form-row mt-4">
          <div class="col-md">
            <validate tag="div">
              <label for="province_id">Provinsi</label>
              <v-select name="province_id" v-model="model.province" :options="province" @input="changeProvince" placeholder="Provinsi" required></v-select>

              <field-messages name="province_id" show="$invalid && $submitted" class="text-danger">
                <small class="form-text text-success">Looks good!</small>
                <small class="form-text text-danger" slot="required">Provinsi is a required field</small>
              </field-messages>
            </validate>
          </div>
        </div>

        <div class="form-row mt-4">
          <div class="col-md">
            <validate tag="div">
              <label for="city_id">Kabupaten/Kota</label>
              <v-select name="city_id" v-model="model.city" :options="city" @input="changeCity" placeholder="Kabupaten/Kota" required></v-select>

              <field-messages name="city_id" show="$invalid && $submitted" class="text-danger">
                <small class="form-text text-success">Looks good!</small>
                <small class="form-text text-danger" slot="required">Kabupaten/Kota is a required field</small>
              </field-messages>
            </validate>
          </div>
        </div>

        <div class="form-row mt-4">
          <div class="col-md">
            <validate tag="div">
              <label for="district_id">Kecamatan</label>
              <v-select name="district_id" v-model="model.district" :options="district" @input="changeDistrict" placeholder="Kecamatan" required></v-select>

                <field-messages name="district_id" show="$invalid && $submitted" class="text-danger">
                <small class="form-text text-success">Looks good!</small>
                <small class="form-text text-danger" slot="required">Kecamatan is a required field</small>
              </field-messages>
            </validate>
          </div>
        </div>

        <div class="form-row mt-4">
          <div class="col-md">
            <validate tag="div">
              <label for="village_id">Kelurahan/Desa</label>
              <v-select name="village_id" v-model="model.village" :options="village" placeholder="Kelurahan/Desa" required></v-select>

              <field-messages name="village_id" show="$invalid && $submitted" class="text-danger">
                <small class="form-text text-success">Looks good!</small>
                <small class="form-text text-danger" slot="required">Kelurahan/Desa is a required field</small>
              </field-messages>
            </validate>
          </div>
        </div>

        <div class="form-row mt-4">
          <div class="col-md">
            <validate tag="div">
              <label for="no_telp">Nomor Telepon</label>
              <input type="text" class="form-control" name="no_telp" v-model="model.no_telp" placeholder="Nomor Telepon" required>

              <field-messages name="no_telp" show="$invalid && $submitted" class="text-danger">
                <small class="form-text text-success">Looks good!</small>
                <small class="form-text text-danger" slot="required">Nomor Telepon is a required field</small>
              </field-messages>
            </validate>
          </div>
        </div>

        <div class="form-row mt-4">
          <div class="col-md">
            <validate tag="div">
              <label for="email">Email</label>
              <input type="text" class="form-control" name="email" v-model="model.email" placeholder="Email" required>

              <field-messages name="email" show="$invalid && $submitted" class="text-danger">
                <small class="form-text text-success">Looks good!</small>
                <small class="form-text text-danger" slot="required">Email is a required field</small>
              </field-messages>
            </validate>
          </div>
        </div>

        <div class="form-row mt-4">
          <div class="col-md">
            <validate tag="div">
              <label for="kode_zona">Zona</label>
              <v-select name="kode_zona" v-model="model.master_zona" :options="master_zona" placeholder="Zona" required></v-select>

              <field-messages name="kode_zona" show="$invalid && $submitted" class="text-danger">
                <small class="form-text text-success">Looks good!</small>
                <small class="form-text text-danger" slot="required">Zona is a required field</small>
              </field-messages>
            </validate>
          </div>
        </div>

        <div class="form-row mt-4">
          <div class="col-md">
            <validate tag="div">
              <label for="uuid">UUID</label>
              <input type="text" class="form-control" name="uuid" v-model="model.uuid" placeholder="UUID" required>

              <field-messages name="uuid" show="$invalid && $submitted" class="text-danger">
                <small class="form-text text-success">Looks good!</small>
                <small class="form-text text-danger" slot="required">UUID is a required field</small>
              </field-messages>
            </validate>
          </div>
        </div>

        <div class="form-row mt-4">
          <div class="col-md">
            <validate tag="div">
              <label for="user_id">Username</label>
              <v-select name="user_id" v-model="model.user" :options="user" placeholder="Username" required></v-select>

              <field-messages name="user_id" show="$invalid && $submitted" class="text-danger">
                <small class="form-text text-success">Looks good!</small>
                <small class="form-text text-danger" slot="required">User is a required field</small>
              </field-messages>
            </validate>
          </div>
        </div>

        <div class="form-row mt-4">
          <div class="col-md">
            <button type="submit" class="btn btn-primary">Submit</button>
            <button type="reset" class="btn btn-secondary" @click="reset">Reset</button>
          </div>
        </div>
      </vue-form>
    </div>
  </div>
</template>

<script>
import swal from 'sweetalert2';

export default {
  data() {
    return {
      state: {},
      title: 'Add Sekolah',
      model: {
        nama                : '',
        npsn                : '',
        jenis_sekolah_id    : '',
        alamat              : '',
        logo                : '',
        foto_gedung         : '',
        province_id         : '',
        city_id             : '',
        district_id         : '',
        village_id          : '',
        no_telp             : '',
        email               : '',
        kode_zona           : '',
        uuid                : '',
        user_id             : '',
        created_at          : '',
        updated_at          : '',

        jenis_sekolah         : '',
        province              : '',
        city                  : '',
        district              : '',
        village               : '',
        master_zona           : '',
        user                  : '',

        province_id_onchange  : 0,
        city_id_onchange      : 0,
        district_id_onchange  : 0,
        village_id_onchange   : 0,
      },
      jenis_sekolah : [],
      province      : [],
      city          : [],
      district      : [],
      village       : [],
      master_zona   : [],
      user          : [],
    }
  },
  mounted(){
    let app = this;

    axios.get('api/sekolah/create')
      .then(response => {
        if (response.data.status == true && response.data.error == false) {
          this.model.user   = response.data.current_user;

          if (response.data.user_special == true) {
            this.user = response.data.users;
          } else {
            this.user.push(response.data.users);
          }
        } else {
          swal(
            'Failed',
            'Oops... '+response.data.message,
            'error'
          );

          app.back();
        }
      })
      .catch(function(response) {
        swal(
          'Not Found',
          'Oops... Your page is not found.',
          'error'
        );

        app.back();
      });

    axios.get('api/jenis-sekolah/get')
      .then(response => {
        if (response.data.status == true && response.data.error == false) {
          this.jenis_sekolah = response.data.jenis_sekolahs;
        } else {
          swal(
            'Failed',
            'Oops... '+response.data.message,
            'error'
          );

          app.back();
        }
      })
      .catch(function(response) {
        swal(
          'Not Found',
          'Oops... Your page is not found.',
          'error'
        );

        app.back();
      });

    axios.get('api/wilayah-indonesia/province/get')
      .then(response => {
        if (response.data.status == true && response.data.error == false) {
          this.province = response.data.provinces;
        } else {
          swal(
            'Failed',
            'Oops... '+response.data.message,
            'error'
          );

          app.back();
        }
      })
      .catch(function(response) {
        swal(
          'Not Found',
          'Oops... Your page is not found.',
          'error'
        );

        app.back();
      });

    axios.get('api/master-zona/get')
      .then(response => {
        if (response.data.status == true && response.data.error == false) {
          this.master_zona = response.data.master_zonas;
        } else {
          swal(
            'Failed',
            'Oops... '+response.data.message,
            'error'
          );

          app.back();
        }
      })
      .catch(function(response) {
        swal(
          'Not Found',
          'Oops... Your page is not found.',
          'error'
        );

        app.back();
      });
  },
  methods: {
    onSubmit: function() {
      let app = this;

      if (this.state.$invalid) {
        return;
      } else {
        axios.post('api/sekolah', {
            nama              : this.model.nama,
            npsn              : this.model.npsn,
            jenis_sekolah_id  : this.model.jenis_sekolah.id,
            alamat            : this.model.alamat,
            // logo              : this.model.logo,
            // foto_gedung       : this.model.foto_gedung,
            province_id       : this.model.province.id,
            city_id           : this.model.city.id,
            district_id       : this.model.district.id,
            village_id        : this.model.village.id,
            no_telp           : this.model.no_telp,
            email             : this.model.email,
            uuid              : this.model.uuid,
            kode_zona         : this.model.master_zona.id,
            user_id           : this.model.user.id,
          })
          .then(response => {
            if (response.data.status == true) {
              if (response.data.error == false) {
                swal(
                  'Created',
                  'Yeah!!! Your data has been created.',
                  'success'
                );

                app.back();
              } else {
                swal(
                  'Failed',
                  'Oops... '+response.data.message,
                  'error'
                );
              }
            } else {
              swal(
                'Failed',
                'Oops... '+response.data.message,
                'error'
              );

              app.back();
            }
          })
          .catch(function(response) {
            swal(
              'Not Found',
              'Oops... Your page is not found.',
              'error'
            );

            app.back();
          });
      }
    },
    changeProvince() {
      if (typeof(this.model.province.id) === 'undefined') {
        this.model.city = '';
      } else {
        if (this.model.province_id_onchange == 0) {
          this.model.province_id_onchange++;
        } else {
          this.model.city = '';
        }

        axios.get('api/wilayah-indonesia/city/get/by-province/'+this.model.province.id)
          .then(response => {
            if (response.data.status == true && response.data.error == false) {
              this.city = response.data.cities;
            }
          });
      }
    },
    changeCity() {
      if (typeof(this.model.city.id) === 'undefined') {
        this.model.district = '';
      } else {
        if (this.model.district_id_onchange == 0) {
          this.model.district_id_onchange++;
        } else {
          this.model.district = '';
        }

        axios.get('api/wilayah-indonesia/district/get/by-city/'+this.model.city.id)
          .then(response => {
            if (response.data.status == true && response.data.error == false) {
              this.district = response.data.districts;
            }
          });
      }
    },
    changeDistrict() {
      if (typeof(this.model.district.id) === 'undefined') {
        this.model.village = '';
      } else {
        if (this.model.village_id_onchange == 0) {
          this.model.village_id_onchange++;
        } else {
          this.model.village = '';
        }

        axios.get('api/wilayah-indonesia/village/get/by-district/'+this.model.district.id)
          .then(response => {
            if (response.data.status == true && response.data.error == false) {
              this.village = response.data.villages;
            }
          });
      }
    },
    reset() {
      this.model = {
        nama              : '',
        npsn              : '',
        jenis_sekolah_id  : '',
        alamat            : '',
        logo              : '',
        foto_gedung       : '',
        province_id       : '',
        city_id           : '',
        district_id       : '',
        village_id        : '',
        no_telp           : '',
        email             : '',
        kode_zona         : '',
        uuid              : '',
        user_id           : '',
        created_at        : '',
        updated_at        : '',

        jenis_sekolah     : '',
        province          : '',
        city              : '',
        district          : '',
        village           : '',
        master_zona       : '',
        user              : '',
      };
    },
    back() {
      window.location = '#/admin/sekolah';
    }
  }
}
</script>
