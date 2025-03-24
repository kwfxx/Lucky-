import requests
import random
import requests
import os
import re
import random
import time

class Agent:
    @staticmethod
    def user():
        aa = {
            "28/9": ["720dpi", "1080dpi", "1440dpi"],
            "29/10": ["720dpi", "1080dpi", "1440dpi", "2160dpi"],
            "30/11": ["1080dpi", "1440dpi", "2160dpi"],
            "31/12": ["1440dpi", "2160dpi"]
        }
        ss = {
            "720dpi": ["1280x720", "1920x1080"],
            "1080dpi": ["1920x1080", "2560x1440", "3840x2160"],
            "1440dpi": ["2560x1440", "3840x2160"],
            "2160dpi": ["3840x2160", "7680x4320"]
        }
        dd = {
            "samsung": ["SM-T292", "SM-G973F", "SM-A515F"],
            "google": ["Pixel 4", "Pixel 5"],
            "huawei": ["P30 Pro", "Mate 40 Pro"],
            "xiaomi": ["Mi 10", "Redmi Note 10"],
            "oneplus": ["8T", "9 Pro"],
            "sony": ["XZ2", "Xperia 1"]
        }
        cc = ["qcom", "exynos", "kirin", "mediatek", "apple"]
        lan = ["en_US", "es_ES", "fr_FR", "de_DE", "zh_CN", "ja_JP", "ko_KR"]
        dp = ["phone", "tablet", "watch", "tv", "car"]
        arm = ["arm64_v8a", "armeabi-v7a", "x86", "x86_64"]
        comb = ["samsung", "google", "huawei", "xiaomi", "oneplus", "sony"]

        sos = random.choice(list(aa.keys()))
        vlo = random.choice(aa[sos])
        lop = random.choice(ss[vlo])
        ki = random.choice(comb)
        mo = random.choice(dd.get(ki, ["Unknown"]))

        user_agent = (
            f"Instagram 351.0.0.41.106 Android "
            f"({sos}; {vlo}; {lop}; {ki}; {mo}; "
            f"{random.choice(arm)}; {random.choice(dp)}; "
            f"{random.choice(lan)}; {random.choice(cc)})"
        )

        return user_agent
        

def Login(user, pas):
    
    try:
        response = requests.post("https://i.instagram.com/api/v1/bloks/apps/com.bloks.www.bloks.caa.login.async.send_login_request/", data={
  'params': "{\"client_input_params\":{\"sim_phones\":[],\"secure_family_device_id\":\"\",\"has_granted_read_contacts_permissions\":0,\"auth_secure_device_id\":\"\",\"has_whatsapp_installed\":1,\"password\":\"#PWD_INSTAGRAM:0:"+str(int(time.time()))+":"+pas+"\",\"sso_token_map_json_string\":\"\",\"event_flow\":\"login_manual\",\"password_contains_non_ascii\":\"false\",\"client_known_key_hash\":\"\",\"encrypted_msisdn\":\"\",\"has_granted_read_phone_permissions\":0,\"app_manager_id\":\"\",\"should_show_nested_nta_from_aymh\":0,\"device_id\":\"android-70301baa15f90dc8\",\"login_attempt_count\":1,\"machine_id\":\"Z49RuQABAAH24qHTKgLLYe-YXrjK\",\"flash_call_permission_status\":{\"READ_PHONE_STATE\":\"DENIED\",\"READ_CALL_LOG\":\"DENIED\",\"ANSWER_PHONE_CALLS\":\"DENIED\"},\"accounts_list\":[],\"family_device_id\":\"e822298a-472f-4fe4-8dff-126a350e8850\",\"fb_ig_device_id\":[],\"device_emails\":[],\"try_num\":1,\"lois_settings\":{\"lois_token\":\"\"},\"event_step\":\"home_page\",\"headers_infra_flow_id\":\"\",\"openid_tokens\":{},\"contact_point\":\""+user+"\"},\"server_params\":{\"should_trigger_override_login_2fa_action\":0,\"is_from_logged_out\":0,\"should_trigger_override_login_success_action\":0,\"login_credential_type\":\"none\",\"server_login_source\":\"login\",\"waterfall_id\":\"73e94377-61eb-4c9b-93e0-7b70e6de8cc2\",\"login_source\":\"Login\",\"is_platform_login\":0,\"INTERNAL__latency_qpl_marker_id\":36707139,\"offline_experiment_group\":\"caa_iteration_v3_perf_ig_4\",\"is_from_landing_page\":0,\"password_text_input_id\":\"6e8frp:103\",\"is_from_empty_password\":0,\"is_from_msplit_fallback\":0,\"ar_event_source\":\"login_home_page\",\"qe_device_id\":\"2948d949-5663-4696-9a2f-f294ac163cf2\",\"username_text_input_id\":\"6e8frp:102\",\"layered_homepage_experiment_group\":null,\"device_id\":\"android-70301baa15f90dc8\",\"INTERNAL__latency_qpl_instance_id\":3.8670536500248E13,\"reg_flow_source\":\"login_home_native_integration_point\",\"is_caa_perf_enabled\":1,\"credential_type\":\"password\",\"is_from_password_entry_page\":0,\"caller\":\"gslr\",\"family_device_id\":\"e822298a-472f-4fe4-8dff-126a350e8850\",\"is_from_assistive_id\":0,\"access_flow_version\":\"F2_FLOW\",\"is_from_logged_in_switcher\":0}}",
  'bk_client_context': "{\"bloks_version\":\"145bdb95c874a8d81dfe9d44aeff8286378f930f5898c808f8d2f0bb1d931181\",\"styles_id\":\"instagram\"}",
  'bloks_versioning_id': "145bdb95c874a8d81dfe9d44aeff8286378f930f5898c808f8d2f0bb1d931181"
}, headers = {
  'User-Agent': str(Agent.user()),
  'x-bloks-version-id': "145bdb95c874a8d81dfe9d44aeff8286378f930f5898c808f8d2f0bb1d931181",
  'x-ig-nav-chain': "com.bloks.www.caa.login.login_homepage:com.bloks.www.caa.login.login_homepage:1:button:1737445843.642::",
  'x-fb-connection-type': "MOBILE.LTE",
  'x-ig-connection-type': "MOBILE(LTE)",
  'x-ig-app-id': "567067343352427",
  'priority': "u=3",
  'accept-language': "en-US",
 })

        msg = str(response.text).replace("/", "").replace("\\", "").encode("utf-8").decode("unicode-escape", errors="ignore")
        ok = re.search(r'Bearer\s([A-Za-z0-9:.]+)', str(msg))

        if "login_success" in msg and ok:
            Acctok = f"Bearer {ok.group(1)}"
            return Acctok
        elif "Incorrect Password" in msg:
            return ("Password Is Incorrect")
        elif "challenge_required" in msg or "checkpoint_challenge_required" in msg:
            return ("OTP")
        elif "Can't find account" in msg:
            return ("No Account")
        else:
        	return (msg)

    except Exception as e:
        print(f"Error with user {user}: {e}")




def Search(query, Acctok):    
    usernames = []
    next_page = None
    rank_token = None

    headers = {
        'User-Agent': "Instagram 351.0.0.41.106 Android (30/11; 440dpi; 1080x2220; Xiaomi/Redmi; Redmi Note 8 Pro; begonia; mt6785; en-US; 647663441)",
        'x-bloks-version-id': "145bdb95c874a8d81dfe9d44aeff8286378f930f5898c808f8d2f0bb1d931181",
        'x-ig-app-id': "567067343352427",
        'priority': "u=3",
        'accept-language': "en-US",
        'authorization': str(Acctok),
    }

    params = {
        'search_surface': "user_serp",
        'timezone_offset': "10800",
        'count': "30",
        'query': query,
    }

    response = requests.get(
        "https://i.instagram.com/api/v1/fbsearch/account_serp/",
        params=params,
        headers=headers
    )

    if response.status_code != 200:
        print(f"Error: {response.status_code}")
        print(response.text)
        exit(0)
    else:
        Ahmed = response.json()

        for user in Ahmed.get('users', []):
            usernames.append(user['username'])

        if Ahmed.get('has_more'):
            next_page = Ahmed.get('page_token')
            rank_token = Ahmed.get('rank_token')

            while next_page:
                params.update({
                    'next_max_id': next_page,
                    'rank_token': rank_token,
                    'page_token': next_page,
                })

                response = requests.get(
                    "https://i.instagram.com/api/v1/fbsearch/account_serp/",
                    params=params,
                    headers=headers
                )

                if response.status_code != 200:
                    print(f"Error: {response.status_code}")
                    print(response.text)
                    break

                Ahmed = response.json()

                for user in Ahmed.get('users', []):
                    usernames.append(user['username'])

                if Ahmed.get('has_more'):
                    next_page = Ahmed.get('page_token')
                    rank_token = Ahmed.get('rank_token')
                else:
                    next_page = None

    return usernames



def main():    
    Acctok = Login(input("Enter Your Username or Email: "), input("Enter Your Password: "))

    if "Bearer" in Acctok: 
        while True: 
            query = "".join(random.choice('qwertyuiopasdfghjklzxcvbnm._') for _ in range(random.randint(2, 9)))

            usernames = Search(query, Acctok)

            for username in usernames:
                print(username)
                with open("Users.txt", "a") as f:
                    f.write(username + "\n")
    else:
        print("Login failed:", Acctok)


if __name__ == "__main__":
    main()
    
