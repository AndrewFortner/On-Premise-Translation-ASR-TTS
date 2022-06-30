# On-Premise-Translation-ASR-TTS
On-premise ASR, speech synthesis, and translation using Facebook self training machine learning models

Once you have downloaded all .py files, naviate to the directory where you have saved the files and type: "pip install -r requirements.txt" on the command line to install required dependencies. This may take some time.

#Supported languages and corresponding codes:
  Arabic (ar_AR), Czech (cs_CZ), German (de_DE), English (en_XX), Spanish (es_XX), 
  Estonian (et_EE), Finnish (fi_FI), French (fr_XX), Gujarati (gu_IN), Hindi (hi_IN),
  Italian (it_IT), Japanese (ja_XX), Kazakh (kk_KZ), Korean (ko_KR), Lithuanian (lt_LT),
  Latvian (lv_LV), Burmese (my_MM), Nepali (ne_NP), Dutch (nl_XX), Romanian (ro_RO),
  Russian (ru_RU), Sinhala (si_LK), Turkish (tr_TR), Vietnamese (vi_VN), Chinese (zh_CN),
  Afrikaans (af_ZA), Azerbaijani (az_AZ), Bengali (bn_IN), Persian (fa_IR), Hebrew (he_IL),
  Croatian (hr_HR), Indonesian (id_ID), Georgian (ka_GE), Khmer (km_KH), Macedonian (mk_MK),
  Malayalam (ml_IN), Mongolian (mn_MN), Marathi (mr_IN), Polish (pl_PL), Pashto (ps_AF),
  Portuguese (pt_XX), Swedish (sv_SE), Swahili (sw_KE), Tamil (ta_IN), Telugu (te_IN), Thai (th_TH),
  Tagalog (tl_XX), Ukrainian (uk_UA), Urdu (ur_PK), Xhosa (xh_ZA), Galician (gl_ES), Slovene (sl_SI)

In order to run the application for ASR using microphone (without translation):
1. Navigate to the directory where you installed asr_translate.py, and type: "uvicorn asr_translate:app" Note that if this is your first time running the program some files will be installed for you. It may take some time as the model is quite large.
2. Wait a couple of seconds for the sever to startup. Once you see the message that says "INFO:     Application startup complete." then the application is ready to run.
3. Go to your local browser and type in "http://127.0.0.1:8000/transcribe-live" (You can alternatively make a GET request to this same URL). The application will now be listening for speech on your microphone.
4. Begin talking and a transcription of your speech will be printed to the console.
5. In order to close the application and see the full transcription, go to "http://127.0.0.1:8000/end" in either a browser or through a GET request, and the full transcription will be returned in JSON format.

In order to run the application for ASR using microphone (with translation):
1. Navigate to the directory where you installed asr_translate.py, and type: "uvicorn asr_translate:app" Note that if this is your first time running the program some files will be installed for you. It may take some time as the model is quite large.
2. Wait a couple of seconds for the sever to startup. Once you see the message that says "INFO:     Application startup complete." then the application is ready to run.
3. Make a POST request to "http://127.0.0.1:8000/translate-live" using a form with name:value pair "out_lang":(desired output language key above). The application will now be listening for speech on your microphone.
4. Begin talking and a transcription of your speech will be printed to the console.
5. In order to close the application and see the full transcription, go to "http://127.0.0.1:8000/end" in either a browser or through a GET request, and the full transcription will be returned in JSON format.

In order to run application for file transcription of a file (without translation):
1. Navigate to the directory where you installed asr_translate.py, and type: "uvicorn asr_translate:app" Note that if this is your first time running the program some files will be installed for you. It may take some time as the model is quite large.
2. Wait a couple of seconds for the sever to startup. Once you see the message that says "INFO:     Application startup complete." then the application is ready to run.
3. Make a POST request to "http://127.0.0.1:8000/transcribe-file" using a form with integer "sr" as sample rate and wav file "file" as the file you want to trasncribe.
4. Wait for the file to finish processing. The full transcription will be returned in JSON format to http://127.0.0.1:8000/transcribe-file. Typically transcription of a wav file takes about 1.5 seconds of processing for every 1 second of audio in the file.

In order to run application for file transcription of a file (with translation):
1. Navigate to the directory where you installed asr_translate.py, and type: "uvicorn asr_translate:app" Note that if this is your first time running the program some files will be installed for you. It may take some time as the model is quite large.
2. Wait a couple of seconds for the sever to startup. Once you see the message that says "INFO:     Application startup complete." then the application is ready to run.
3. Make a POST request to "http://127.0.0.1:8000/translate-transcription" using a form with integer "sr" as sample rate and wav file "file" as the file you want to trasncribe and with name:value pair "out_lang":(desired output language key above).
4. Wait for the file to finish processing. The full transcription will be returned in JSON format to http://127.0.0.1:8000/translate-transcription. Typically transcription of a wav file takes about 1.5 seconds of processing for every 1 second of audio in the file.

In order to run application for text to speech (without translation):
1. Navigate to the directory where you installed tts_fastspeech2.py, and type: "uvicorn tts_fastspeech2:app" Note that if this is your first time running the program some files will be installed for you. It may take some time as the model is quite large.
2. Wait a couple of seconds for the sever to startup. Once you see the message that says "INFO:     Application startup complete." then the application is ready to run.
3. Make a POST request to "http://127.0.0.1:8000/synthesize" using a form with string "text" as the text you want to synthesize.
4. Wait for the file to finish processing. The full transcription will be returned in JSON format to http://127.0.0.1:8000/synthesize.

In order to run application for text to speech (with translation):
1. Navigate to the directory where you installed tts_fastspeech2.py, and type: "uvicorn tts_fastspeech2:app" Note that if this is your first time running the program some files will be installed for you. It may take some time as the model is quite large.
2. Wait a couple of seconds for the sever to startup. Once you see the message that says "INFO:     Application startup complete." then the application is ready to run.
3. Make a POST request to "http://127.0.0.1:8000/synthesize-translation" using a form with string "text" as the text you want to synthesize, string "in_lang" with input language key (above), and "out_lang" with output language key (above).
4. Wait for the file to finish processing. The full transcription will be returned in JSON format to http://127.0.0.1:8000/synthesize-translation.
