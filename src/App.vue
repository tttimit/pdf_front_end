<template>
  <div id="app" style="padding-bottom: 50px">
    <el-container
      style="max-width: 1000px; min-width: 600px; border: 1px solid #eee; justify: center;"
    >
      <el-header style="text-align: Left; font-size: 20px">
        <span>Form Generator</span>
        <span style="margin-left: 20px">此Demo仅作功能演示之用，因时间仓促，样式未设置；输入内容合法性未进行检查。</span>
        <!-- <el-dropdown>
            <i class="el-icon-setting" style="margin-right: 15px"></i>
            <el-dropdown-menu slot="dropdown">
              <el-dropdown-item>查看</el-dropdown-item>
              <el-dropdown-item>新增</el-dropdown-item>
              <el-dropdown-item>删除</el-dropdown-item>
            </el-dropdown-menu>
          </el-dropdown>
        <span>王小虎</span>-->
      </el-header>
      <el-container>
        <el-aside width="200px" style="background-color: rgb(238, 241, 246)">
          <el-menu
            default-active="1-4-1"
            class="el-menu-vertical-demo"
            @open="handleOpen"
            @close="handleClose"
            :collapse="isCollapse"
          >
            <el-submenu index="1">
              <template slot="title">
                <i class="el-icon-location"></i>
                <span slot="title">Form 1022</span>
              </template>
              <el-menu-item-group>
                <el-menu-item index="1-1">Your Details</el-menu-item>
                <el-menu-item index="1-2">Other Applicants</el-menu-item>
                <el-menu-item index="1-3">Extra Infomations</el-menu-item>
              </el-menu-item-group>
            </el-submenu>

            <el-submenu index="2">
              <template slot="title">
                <i class="el-icon-location"></i>
                <span slot="title">Other Form</span>
              </template>
              <el-menu-item-group>
                <el-menu-item index="2-1">Not implement</el-menu-item>
                <el-menu-item index="2-2">Not implement</el-menu-item>
                <el-menu-item index="2-3">Not implement</el-menu-item>
              </el-menu-item-group>
            </el-submenu>
          </el-menu>
        </el-aside>

        <!-- 主页内容 start -->
        <el-main>
          <el-form ref="form" :model="form" label-width="160px" label-position="left">
            <div class="div-title">Your Full Name</div>
            <el-form-item>
              <el-form-item label="Last Name">
                <el-col :span="18">
                  <el-input v-model="ap.name_fam"></el-input>
                </el-col>
              </el-form-item>

              <el-form-item label="Given Names">
                <el-col :span="18">
                  <el-input v-model="ap.name_giv"></el-input>
                </el-col>
              </el-form-item>
            </el-form-item>
            <el-form-item label="Date of birth">
              <el-col :span="5">-</el-col>
              <el-col :span="11">
                <el-date-picker
                  type="date"
                  placeholder="选择日期"
                  v-model="ap.dob"
                  style="width: 100%;"
                ></el-date-picker>
              </el-col>
            </el-form-item>

            <div class="div-title">Place of birth</div>

            <el-form-item>
              <el-form-item label="Town/City">
                <el-col :span="18">
                  <el-input v-model="ap.birth_town"></el-input>
                </el-col>
              </el-form-item>

              <el-form-item label="Country">
                <el-col :span="18">
                  <el-input v-model="ap.birth_cntry"></el-input>
                </el-col>
              </el-form-item>
            </el-form-item>

            <el-form-item label="Relationship status">
              <el-checkbox-group v-model="ap.relations">
                <el-checkbox label="Married" name="ap.marital_mar"></el-checkbox>
                <el-checkbox label="Engaged" name="ap.marital_eng"></el-checkbox>
                <el-checkbox label="De facto" name="ap.marital_def"></el-checkbox>
                <el-checkbox label="Separated" name="ap.marital_sep"></el-checkbox>
                <el-checkbox label="Divorced" name="ap.marital_div"></el-checkbox>
                <el-checkbox label="Widowed" name="ap.marital_wid"></el-checkbox>
                <el-checkbox
                  label="Never married or been in a de facto relationship"
                  name="ap.marital_nev_mar"
                ></el-checkbox>
              </el-checkbox-group>
            </el-form-item>

            <div class="div-title">Detail of passport</div>
            <el-form-item>
              <el-col :span="18">
                <el-form-item label="Passport number">
                  <el-input v-model="ap.pass_no"></el-input>
                </el-form-item>
              </el-col>
              <el-col :span="18">
                <el-form-item label="Country of passport">
                  <el-input v-model="ap.pass_cntry"></el-input>
                </el-form-item>
              </el-col>
            </el-form-item>

            <el-form-item label="Identity information">
              <el-col :span="18">
                <el-form-item label="Identity number">
                  <el-input v-model="ap.ident_no"></el-input>
                </el-form-item>
              </el-col>
              <el-col :span="18">
                <el-form-item label="Country of issue">
                  <el-input v-model="ap.ident_cntry"></el-input>
                </el-form-item>
              </el-col>
            </el-form-item>

            <el-form-item label="Your current country of citizenship">
              <el-col :span="5">-</el-col>
              <el-col :span="10">
                <el-input v-model="ap.cit"></el-input>
              </el-col>
            </el-form-item>

            <el-form-item label="Your current residential Address" label-width="200px">
              <el-col :span="3">-</el-col>
              <el-col :span="19">
                <el-form-item label>
                  <el-input v-model="ap.resi_tr" placeholder="street"></el-input>
                </el-form-item>
                <el-form-item label>
                  <el-input v-model="ap.resi_sub" placeholder="town/city"></el-input>
                </el-form-item>
                <el-form-item label>
                  <el-input v-model="ap.resi_cntry" placeholder="state"></el-input>
                </el-form-item>
                <el-form-item label>
                  <el-input v-model="ap.resi_pc" placeholder="postcode"></el-input>
                </el-form-item>
              </el-col>
            </el-form-item>

            <div
              style="text-align: left"
            >Your current residential Address (If the same as your residential address, write 'AS ABOVE')</div>
            <el-form-item style="margin-top: 10px">
              <el-col :span="19">
                <el-form-item>
                  <el-input v-model="ap.corresp_str" placeholder="street"></el-input>
                </el-form-item>

                <el-form-item>
                  <el-input v-model="ap.corresp_sub" placeholder="town/city"></el-input>
                </el-form-item>

                <el-form-item>
                  <el-input v-model="ap.corresp_cntry" placeholder="state"></el-input>
                </el-form-item>
              
              <el-form-item label>
                  <el-input v-model="ap.corresp_hap" placeholder="postcode"></el-input>
                </el-form-item>
                </el-col>
            </el-form-item>

            <div class="div-title">Your telephone numbers</div>
              <el-form-item label="Office hours">
                <el-col :span="6">
                  <el-input v-model="ap.off_ph_cc" placeholder="Country code"></el-input>
                </el-col>
                <el-col :span="6">
                  <el-input v-model="ap.off_ph_ac" placeholder="Area code"></el-input>
                </el-col>
                <el-col :span="12">
                  <el-input v-model="ap.off_ph" placeholder="Number"></el-input>
                </el-col>
              </el-form-item>
              <el-form-item label="After hours">
                <el-col :span="6">
                  <el-input v-model="ap.after_ph_cc" placeholder="Country code"></el-input>
                </el-col>
                <el-col :span="6">
                  <el-input v-model="ap.after_ph_ac" placeholder="Area code"></el-input>
                </el-col>
                <el-col :span="12">
                  <el-input v-model="ap.off_pn" placeholder="Number"></el-input>
                </el-col>
              </el-form-item>
            

            <div>Do you agree to the Department communicating with you by fax, email or other electronic means?</div>

            <el-form-item label="Your choice">
              <el-radio v-model="ap.com_dimia" label="no">No</el-radio>
              <el-radio v-model="ap.com_dimia" label="yes">Yes</el-radio>
            </el-form-item>
            <el-form-item label="Fax number" v-if="ap.com_dimia === 'yes'">
              <el-col :span="6">
                <el-input v-model="ap.fax_cc" placeholder="Country code"></el-input>
              </el-col>
              <el-col :span="6">
                <el-input v-model="ap.fax_ac" placeholder="Area code"></el-input>
              </el-col>
              <el-col :span="12">
                <el-input v-model="ap.fax_ph" placeholder="Number"></el-input>
              </el-col>
            </el-form-item>
            <el-form-item label="Email address" v-if="ap.com_dimia === 'yes'">
              <el-input v-model="ap.email"></el-input>
            </el-form-item>

            <div
              style="text-align: left"
            >Client number of file number issued to you by the Department (if known)</div>
            <el-form-item style="margin: 10px">
              <el-input v-model="ap.file_no"></el-input>
            </el-form-item>
          </el-form>
          <el-row>
            <el-button type="primary" @click="onSubmit">提交本页</el-button>
          </el-row>
        </el-main>
        <!-- 主页内容 end -->
      </el-container>
    </el-container>
  </div>
</template>

<script>
export default {
  data() {
    const item = {};
    return {
      ap: {
        name_fam:'',
        name_giv:'',
        dob:'',
        birth_town:'',
        birth_cntry:'',
        relations: [],
        pass_no:'',
        pass_cntry: '',
        ident_no:'',
        ident_cntry:'',
        cit:'', // citizenship
        resi_tr:'',
        resi_sub:'',
        resi_cntry:'',
        resi_pc:'',
        corresp_str:'',
        corresp_sub:'',
        corresp_cntry:'',
        corresp_hap:'',
        off_ph_cc:'',
        off_ph_ac:'',
        off_ph:'',
        after_ph_cc:'',
        after_ph_ac:'',
        off_pn:'',
        com_dimia:'', // yes or no
        fax_cc:'',
        fax_ac:'',
        fax_ph:'',
        email:'',
        file_np:''
      }
    };
  },
  methods: {
    onSubmit() {
      console.log("submit!");
    }
  }
};
</script>

<style>
#app {
  font-family: Helvetica, sans-serif;
  text-align: center;
}
.el-header {
  background-color: #b3c0d1;
  color: #333;
  line-height: 60px;
}

.div-title {
  text-align: left;
}

.el-aside {
  color: #333;
}

.el-col {
  border-radius: 4px;
}
</style>
