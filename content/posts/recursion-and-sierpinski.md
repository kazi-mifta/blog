+++
autoCollapseToc = false
categories = []
comment = true
date = 2020-03-10T18:00:00Z
description = ""
draft = true
featured_image = ""
featured_image_preview = ""
license = ""
math = false
show_description = false
show_in_homepage = true
tags = []
title = "Recursion and Sierpinski"
toc = false

+++
কলেজ থেকেই theory আর euqation গুলো সহজে মাথায় ঢুকত না । তাই গল্প পড়ে পড়ে বুঝার চেষ্টা করতাম যে জিনিসটা কিভাবে আসল, কোথাই দরকার পড়েছিল।ইউনিভার্সিটিতে ১ম বর্ষে যখন recursion পড়ান হয়েছিল কিছুই বুঝতে পারিনি তখন । নিজেই নিজেকে call করে এটাই নাকি recursion । খুব উদ্ভট আর দুর্বোধ্য মনে হচ্ছিল তখন । চিন্তা করেছিলাম যে, যেখানেই recursion আসবে loop দিয়ে কাজ চালিয়ে নেব। কিন্তু দিন দিন recursion এর আনাগোনা বাড়তে থাকল । ধীরে ধীরে ঘাটাঘাটি করার পর যেন একটু ধরতে পারলাম বিষয়টা। বহু উদাহরণ দেখার পর বিষয়টি আস্তে আস্তে মাথাই ধরা দিল। এই কয়েকদিন আগে Computer graphics lab এ চোখের সামনে recursion কে আবার দেখলাম ,বিভিন্ন রকম আজগুবি সব ছবি তৈরি করে দিচ্ছে । Recursion এর সৌন্দর্যকে ধরতে পারলাম সেইসময় । তখন মনে হল এভাবে যদি ১ম বর্ষে বুঝানো হত, তাইলে আমি হইত loop এর জাইগায় recursion বেশি ব্যবহার করতাম ।

উদাহরণ দেখার আগে Recursion এর শুরুর দিককার একটি গল্প বলে নিই -

১৯৫০ সালের দিককার কথা, তখনকার দিনে এক এক কম্পিউটারে এক এক রকম প্রোগ্রামিং ল্যাঙ্গুয়েজ ব্যবহার করতে হত। কম্পিউটার নির্মাতারা যেসব দিকনির্দেশনা দিতেন সেগুলো অনুসরণ করতে হত । এক এক কম্পিউটারে এক এক রকম দিকনির্দেশনা থাকা আসলেই অনেক সমস্যা। একজন তার কম্পিউটারে করা প্রোগ্রাম, আরেকজনের কম্পিউটারে চালাতে পারতেন না। এ ঝামেলা থেকে রেহাই পেতে IFIP (International Federation for Information Processing) সব নামকরা কম্পিউটার বিজ্ঞানী আর গণিতবিদদের নিয়েএকটি কমিটি গঠন করে । এ কমিটির কাজ ছিল এমন একটি প্রোগ্রামিং ল্যাঙ্গুয়েজ তৈরি করা যেটা কিনা যেকোনো কম্পিউটার এ চলে । তারা এ ল্যাঙ্গুয়েজ এর নামে দিল ALGOL ।

শুরু হল ল্যাঙ্গুয়েজ তৈরির কাজ । সেসময় John McCarthy কেবল মাত্র তার উদ্ভাবিত LISP ল্যাঙ্গুয়েজ এর কাজ শেষ করেছেন, তিনিও এ কমিটির একজন সদস্য ছিলেন । Lisp যেকোনো কম্পিউটারে চলতো, কাড়ন এটা interpreter ব্যবহার করত । কিন্তু Lisp শুধু মাত্র তার ইউনিভার্সিটির গণ্ডিতেই সীমাবদ্ধ ছিল। তখন এটা সার্বজনীন ছিল না। LISP এ recursion ব্যবহার হত , তাই John McCarthy চাইছিলেন ALGOL এ recursion এর সুবিধা যুক্ত করা হোক । কিন্তু ভেটো দিলেন কমিটির অধিকাংশ বিজ্ঞানী। কমিটিতে অধিকাংশ বিজ্ঞানী ছিলেন জার্মান আর তারা চাইছিলেন ALGOL কে কার্যকারী আর দ্রুততম করতে । তাদের মতে recursion যুক্ত করতে হলে এর উপর আরও গবেষণা করা দরকার । এখন recursion সংযুক্ত করলে নাকি সেটা ল্যাঙ্গুয়েজ কে ধীর গতির করে দিতে পারে।

কিন্তু ২ জন বিজ্ঞানী McCarthy এর পক্ষে ছিলেন । Peter Naur আর Adrian Van Wijngaarden । দুইজনেই recursion এর ব্যাপারে খুবই আগ্রহী ছিলেন । Wijngaarden ছিলেন একাধারে কম্পিউটার বিজ্ঞানী আর গণিতবিদ। Peter Naur মহাকাশচারী হতে ছেয়েছিলেন কিন্তু পরে কম্পিউটারের দিকে ঝোঁক চলে আসে। তাদের সাথে ছিলেন আরেক বাঘা কম্পিউটার বিজ্ঞানী, Edsger Wybe Dijkstra । তিনিই আসলে Wijngaarden কে মদদ দিয়েছিলেন যে recursion কে যেন যুক্ত করা হয় ।

Peter Naur ছিলেন ALGOL ল্যাঙ্গুয়েজের ব্যবহার নির্দেশিকা তৈরির দায়িত্বে । Wijngaarden তাকে ফোন দিলেন এবং Dijkstra এর পক্ষ থেকে একটি সংশোধনী প্রস্তাব করেলেন । Wijngaarden আর Dijkstra জানতেন যে এ সংশোধনী যদি অন্যদের চোখে পড়ে তাইলে বিপদ । তাই Dijkstra কথার মারপ্যাঁচে এমন একটি সংশোধনী প্রস্তাব করেন যেটি দেখলেও প্রায় সকলেই এড়িয়ে যাই । কিন্তু জার্মান বিজ্ঞানী Friedrich Ludwig Bauer বিষয়টি ধরে ফেলেন। তিনি এ বিষয়টির তীব্র প্রতিবাদ করেন এবং এ ঘটনাকে“Amsterdam Plot” নামে আখ্যায়িত করেন। তার প্রতিবাদে শেষমেশ সংশোধনী বাতিল করা হই।

কিন্তু recursion কে বাদ দিয়ে রাখা যাইনি । পরবর্তীতে recursion এর ব্যবহার বাড়তে শুরু করে আর ALGOL ল্যাঙ্গুয়েজেও recursion কে জাইগা দেওয়া হই ।

Recursion এর ব্যবহার কিন্তু আরও বহু আগে থেকেই বিদ্যমান। গণিত এ recursive function থেকেই কম্পিউটার প্রোগ্রামের recursion এর উদ্ভব । গণিতের অনেক বিখ্যাত বিষয় এই recursion এর সাথে জড়িত । যেমন - ফিবনাচ্চি ধারা , Sierpinski ত্রিভুজ, Cantor Set ।

Graphics Lab এ দেখান হচ্ছিল Sierpinski Triangle । আর এই ত্রিভুজ তৈরির কাজটি খুব সুন্দর ভাবে recursion করে দিচ্ছিল ।

    # define GL_SILENCE_DEPRECATION
    #ifdef __APPLE_CC__
    #include <GLUT/glut.h>
    #else
    #include <GL/glut.h>
    #endif
    
    void display() {
    
      glClear(GL_COLOR_BUFFER_BIT);
    
      glBegin(GL_POLYGON);
        glColor3f(1, 0, 0); glVertex3f(-0.6, -0.75, 0.5);
        glColor3f(0, 1, 0); glVertex3f(0.6, -0.75, 0);
        glColor3f(0, 0, 1); glVertex3f(0, 0.75, 0);
      glEnd();
    
      glFlush();
    }
    
    int main(int argc, char** argv) {
      glutInit(&argc, argv);
      glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB);
    
      glutInitWindowPosition(80, 80);
      glutInitWindowSize(400, 300);
      glutCreateWindow("A Simple Triangle");
    
      glutDisplayFunc(display);
      glutMainLoop();
    }