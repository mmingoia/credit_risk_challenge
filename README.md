# credit_risk_challenge

UTDA Module 17

## Challenge Writeup

For this challenge I used 4 different sampling methods to find the most useful method in identifying high risk loans. The details from each of the four sampling methods: Random Oversampling, SMOTE oversampling, undersampling, and combination sampling are below.

Due to the fact that the large majority of the loads from the dataset are low risk, the precision of the models in identifying low risk loans are very high, typically 0.99 or 1.00 and the precision for the high risk loans is very low, 0.01 in all of the sampling methods.  Due to this the most accurate method of evaluating these methods is the Balanced accuracy score, which averages the recall for both high and low risk loans.  This gives a better indication of the methods performance.

Each of the methods Balanced accuracy score is below with the confusion matrix and the classification report.  The best performing method is the combination approach using SMOTEENN.  It's Balanced Accuracy Score is 0.68.  This model is reasonably accurate at identifying high risk loans with a 0.77 recall.  However, its recall of low risk loans is 0.59 means that it will identify 41% of the low risk loans as high risk. This model will result in less high risk loan being made, but it will also result in a significant number of low risk loans not being made. If a better method could not be found, this method could work, but I would recommend using one of the methods in the Extension section of the Challenge which has better results.

### Random Oversampling Output

Confusion Matrix
                  Predicted High Risk  Predicted Low Risk
Actual High Risk                   75                  26
Actual Low Risk                  7216                9888

Balanced Accuracy Score : 0.66

Classification Report

                   pre       rec       spe        f1       geo       iba       sup

  high_risk       0.01      0.74      0.58      0.02      0.66      0.44       101
   low_risk       1.00      0.58      0.74      0.73      0.66      0.42     17104

avg / total       0.99      0.58      0.74      0.73      0.66      0.42     17205

### SMOTE Oversampling Output

Confusion Matrix
                  Predicted High Risk  Predicted Low Risk
Actual High Risk                   63                  38
Actual Low Risk                  5410               11694

Balanced Accuracy Score : 0.65

Classification Report

                   pre       rec       spe        f1       geo       iba       sup

  high_risk       0.01      0.62      0.68      0.02      0.65      0.42       101
   low_risk       1.00      0.68      0.62      0.81      0.65      0.43     17104

avg / total       0.99      0.68      0.62      0.81      0.65      0.43     17205

### Undersampling Output (cluster centroids algorithm)

Confusion Matrix
                  Predicted High Risk  Predicted Low Risk
Actual High Risk                   69                  32
Actual Low Risk                 10062                7042

Balanced Accuracy Score : 0.55

Classification Report

                   pre       rec       spe        f1       geo       iba       sup

  high_risk       0.01      0.68      0.41      0.01      0.53      0.29       101
   low_risk       1.00      0.41      0.68      0.58      0.53      0.27     17104

avg / total       0.99      0.41      0.68      0.58      0.53      0.27     17205

### Combination Output (SMOTEENN)

Confusion Matrix
                  Predicted High Risk  Predicted Low Risk
Actual High Risk                   78                  23
Actual Low Risk                  7024               10080

Balanced Accuracy Score : 0.68

Classification Report

                   pre       rec       spe        f1       geo       iba       sup

  high_risk       0.01      0.77      0.59      0.02      0.67      0.46       101
   low_risk       1.00      0.59      0.77      0.74      0.67      0.45     17104

avg / total       0.99      0.59      0.77      0.74      0.67      0.45     17205

## Extension Writeup

Both of these methods have a significantly higher Balanced Accuracy score than the 4 methods discussed in the challenge section.  This strongest model is the "EasyEnsemble" which has a Balanced Accuracy score of 0.93, a recall for the high risk loans of 0.92 and a recall of the low risk loans of 0.94.  This would result in very few bad loans being made and would not reject a large number of low risk loans.

### Balanced Random Forest Output

Confusion Matrix
                  Predicted High Risk  Predicted Low Risk
Actual High Risk                   71                  30
Actual Low Risk                  2153               14951

Balanced Accuracy Score : 0.79

Classification Report

                   pre       rec       spe        f1       geo       iba       sup

  high_risk       0.03      0.70      0.87      0.06      0.78      0.60       101
   low_risk       1.00      0.87      0.70      0.93      0.78      0.62     17104

avg / total       0.99      0.87      0.70      0.93      0.78      0.62     17205

Feature Importance in Descending order

 (0.07876809003486353, 'total_rec_prncp'),
 (0.05883806887524815, 'total_pymnt'),
 (0.05625613759225244, 'total_pymnt_inv'),
 (0.05355513093134745, 'total_rec_int'),
 (0.0500331813446525, 'last_pymnt_amnt'),
 (0.02966959508700077, 'int_rate'),
 (0.021129125328012987, 'issue_d_Jan-2019'),
 (0.01980242888931366, 'installment'),
 (0.01747062730041245, 'dti'),
 (0.016858293184471483, 'out_prncp_inv'),
 (0.01641297102011915, 'total_bal_ex_mort'),
 (0.015220714904737209, 'mths_since_recent_inq'),
 (0.015115240704562424, 'issue_d_Mar-2019'),
 (0.014926655663448373, 'revol_bal'),
 (0.014899352873994727, 'max_bal_bc'),
 (0.014881069023035237, 'out_prncp'),
 (0.014859446582326507, 'mo_sin_old_rev_tl_op'),
 (0.014832564501144122, 'annual_inc'),
 (0.014613819728800227, 'bc_util'),
 (0.014487685026878092, 'tot_hi_cred_lim'),
 (0.013921085423763812, 'mo_sin_old_il_acct'),
 (0.013534131593418711, 'mths_since_rcnt_il'),
 (0.013364759441576994, 'total_rev_hi_lim'),
 (0.01332289882475225, 'avg_cur_bal'),
 (0.013265926832893358, 'bc_open_to_buy'),
 (0.01311545089813887, 'il_util'),
 (0.01304530062898567, 'total_bc_limit'),
 (0.0130446065288952, 'all_util'),
 (0.013030046723135838, 'pct_tl_nvr_dlq'),
 (0.012855901280381887, 'tot_cur_bal'),
 (0.01279908506759016, 'total_il_high_credit_limit'),
 (0.012773576514405109, 'inq_last_12m'),
 (0.011968994260747247, 'total_bal_il'),
 (0.010982948025240226, 'mo_sin_rcnt_tl'),
 (0.010579906006851516, 'loan_amnt'),
 (0.010575363106694519, 'mths_since_recent_bc'),
 (0.010320067009550682, 'num_rev_accts'),
 (0.010209212170253059, 'total_acc'),
 (0.009753839399393215, 'open_acc_6m'),
 (0.009662050208879065, 'num_il_tl'),
 (0.009632472481996241, 'num_actv_rev_tl'),
 (0.009393346012674945, 'mo_sin_rcnt_rev_tl_op'),
 (0.00872448189550355, 'num_bc_tl'),
 (0.008628938824946404, 'num_sats'),
 (0.008330966254402506, 'num_op_rev_tl'),
 (0.007570544824579072, 'num_bc_sats'),
 (0.007548811505974241, 'num_tl_op_past_12m'),
 (0.007489717491934961, 'open_act_il'),
 (0.007382231721841728, 'open_acc'),
 (0.007272665006598051, 'num_rev_tl_bal_gt_0'),
 (0.006998827313196186, 'total_rec_late_fee'),
 (0.006866662924995743, 'num_actv_bc_tl'),
 (0.006714495620628373, 'acc_open_past_24mths'),
 (0.006561432872333855, 'open_il_24m'),
 (0.006240598451492287, 'inq_fi'),
 (0.006216409633238659, 'inq_last_6mths'),
 (0.0061708920490257954, 'mort_acc'),
 (0.006083218608279307, 'total_cu_tl'),
 (0.005640206440873574, 'issue_d_Feb-2019'),
 (0.005634546230136711, 'open_rv_24m'),
 (0.005131046989565006, 'percent_bc_gt_75'),
 (0.005106000423451099, 'next_pymnt_d_Apr-2019'),
 (0.005036652777545191, 'next_pymnt_d_May-2019'),
 (0.004860024796675963, 'open_il_12m'),
 (0.004198582835532627, 'tot_coll_amt'),
 (0.004018916067963884, 'open_rv_12m'),
 (0.0037571920083085985, 'num_accts_ever_120_pd'),
 (0.003082852259926947, 'delinq_2yrs'),
 (0.0029133221443170495, 'home_ownership_RENT'),
 (0.002824523629114469, 'home_ownership_OWN'),
 (0.002204946377565813, 'verification_status_Not Verified'),
 (0.0020912385738361574, 'application_type_Joint App'),
 (0.002015258269512615, 'pub_rec'),
 (0.0019325773153555006, 'verification_status_Verified'),
 (0.001901604006185586, 'application_type_Individual'),
 (0.0015046400907840708, 'verification_status_Source Verified'),
 (0.0014589723334940362, 'home_ownership_MORTGAGE'),
 (0.0013727925120781853, 'pub_rec_bankruptcies'),
 (0.0011520703643731528, 'initial_list_status_w'),
 (0.0011005704165634263, 'initial_list_status_f'),
 (0.0009956935704327383, 'num_tl_90g_dpd_24m'),
 (0.0007150315534652695, 'collections_12_mths_ex_med'),
 (0.0004955956183545533, 'home_ownership_ANY'),
 (0.0002730803587770788, 'chargeoff_within_12_mths'),
 (0.0, 'tax_liens'),
 (0.0, 'recoveries'),
 (0.0, 'pymnt_plan_n'),
 (0.0, 'policy_code'),
 (0.0, 'num_tl_30dpd'),
 (0.0, 'num_tl_120dpd_2m'),
 (0.0, 'hardship_flag_N'),
 (0.0, 'delinq_amnt'),
 (0.0, 'debt_settlement_flag_N'),
 (0.0, 'collection_recovery_fee'),
 (0.0, 'acc_now_delinq')

### EasyEnsemble Output

Confusion Matrix
                  Predicted High Risk  Predicted Low Risk
Actual High Risk                   93                   8
Actual Low Risk                   983               16121

Balanced Accuracy Score : 0.93

Classification Report

                   pre       rec       spe        f1       geo       iba       sup

  high_risk       0.09      0.92      0.94      0.16      0.93      0.87       101
   low_risk       1.00      0.94      0.92      0.97      0.93      0.87     17104

avg / total       0.99      0.94      0.92      0.97      0.93      0.87     17205
