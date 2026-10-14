https://zmk.dev/docs/keymaps/behaviors/hold-tap   

With the current hold-preferred behavior, pressing another key while J is still   
 held can immediately turn J into Shift—even if you meant to type j.               
                                                                                   
 With tap-preferred, that next key press doesn’t immediately trigger Shift. If you 
 release J before the 200 ms tapping term expires, ZMK treats it as j, and the     
 next letter won’t be capitalized. To use J as Shift, you’d hold it past the       
 timeout before pressing the other key.                                            
                                                                                   
 So it helps with quickly rolled keystrokes, but makes quick, overlapping mod-tap  
 chords harder. If J remains held beyond 200 ms, Shift still activates. A global   
 &mt change would also affect the Ctrl mods on D and K; we can define a separate   
 behavior if you want to limit it to F and J.  
