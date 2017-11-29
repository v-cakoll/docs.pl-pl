---
title: "Porady: kompilowanie warunkowe ze śledzeniem i debugowaniem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- trace compiler options
- trace statements
- compiling source code, trace statements
- tracing [.NET Framework], enabling or disabling
- tracing [.NET Framework], compiling conditionally
- TRACE directive
- conditional compilation, tracing code
ms.assetid: 56d051c3-012c-42c1-9a58-7270edc624aa
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f3907888ebcda9c5c6c498cbff39956391f7e213
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a>Porady: kompilowanie warunkowe ze śledzeniem i debugowaniem
Podczas debugowania aplikacji podczas tworzenia Twojej śledzenia i dane wyjściowe debugowania Przejdź w oknie danych wyjściowych w programie Visual Studio. Jednak aby włączyć funkcje śledzenia do wdrożonej aplikacji, należy skompilować instrumentowanej aplikacji przy użyciu **śledzenia** dyrektywy kompilatora włączone. Dzięki temu kod śledzenia ma być kompilowana w wersji aplikacji. Jeśli nie włączysz **śledzenia** dyrektywy, wszystkie kod śledzenia jest ignorowany podczas kompilacji i nie jest objęta kodu wykonywalnego, który zostanie wdrożony.  
  
 Śledzenie i debugowanie metody skojarzony atrybuty warunkowe. Na przykład, jeśli atrybut warunkowej dla śledzenia jest **true**, wszystkie instrukcje śledzenia znajdują się w obrębie zestawu (pliku skompilowanego .exe lub .dll); Jeśli **śledzenia** atrybut conditional jest **false**, instrukcji śledzenia nie są uwzględniane.  
  
 Można mieć **śledzenia** lub **debugowania** atrybut conditional włączone dla kompilacji, lub obie lub nie. W związku z tym istnieją cztery typy kompilacji: **debugowania**, **śledzenia**, zarówno lub nie. Niektóre kompilacjami wydania w przypadku wdrożenia produkcyjnego może zawierać ani; kompilacje debugowania najbardziej zawiera oba.  
  
 Ustawienia kompilatora dla aplikacji na kilka sposobów:  
  
-   Strony właściwości  
  
-   W wierszu polecenia  
  
-   **#CONST** (w języku Visual Basic) i **#define** (dla C#)  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a>Aby zmienić ustawienia kompilacji z okna dialogowego strony właściwości  
  
1.  Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań**.  
  
2.  Wybierz **właściwości** z menu skrótów.  
  
    -   W języku Visual Basic, kliknij przycisk **skompilować** w okienku po lewej stronie właściwości, a następnie kliknij **zaawansowane opcje kompilacji** przycisk, aby wyświetlić **Zaawansowane ustawienia kompilatora**okno dialogowe. Zaznacz pola wyboru dla ustawienia kompilatora, który chcesz włączyć. Wyczyść pola wyboru dla ustawień, które mają zostać wyłączone.  
  
    -   W języku C#, kliknij przycisk **kompilacji** w okienku po lewej stronie właściwości, a następnie zaznacz pola wyboru Ustawienia kompilatora, aby umożliwić. Wyczyść pola wyboru dla ustawień, które mają zostać wyłączone.  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a>Aby skompilować kod instrumentowane przy użyciu wiersza polecenia  
  
1.  Ustawiona przełącznik warunkowego kompilatora w wierszu polecenia. Kompilator będzie zawierać śledzenia lub debugowania kodu w pliku wykonywalnego.  
  
     Na przykład następująca instrukcja kompilatora wprowadzona w wierszu polecenia obejmują kod śledzenia w skompilowanych pliku wykonywalnego:  
  
     W języku Visual Basic: **vbc /r:System.dll /d:TRACE = TRUE /d:DEBUG = FALSE MyApplication.vb**  
  
     Język C#: **csc /r:System.dll /d:TRACE /d:DEBUG = FALSE MyApplication.cs**  
  
    > [!TIP]
    >  Aby skompilować więcej niż jeden plik aplikacji, pozostaw puste miejsce między nazwami plików, na przykład **MyApplication1.vb MyApplication2.vb MyApplication3.vb** lub **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.  
  
     Znaczenie dyrektywy kompilacja warunkowa używane w powyższych przykładach wygląda następująco:  
  
    |Dyrektywy|Znaczenie|  
    |---------------|-------------|  
    |`vbc`|kompilator Visual Basic|  
    |`csc`|Kompilator języka C#|  
    |`/r:`|Odwołuje się do zestawu zewnętrzne (plik EXE lub DLL)|  
    |`/d:`|Określa symbol kompilacji warunkowej|  
  
    > [!NOTE]
    >  Należy pisowni śledzenia i debugowania z wielkich liter. Aby uzyskać więcej informacji na temat poleceń kompilacji warunkowej, wprowadź `vbc /?` (w języku Visual Basic) lub `csc /?` (dla C#) w wierszu polecenia. Aby uzyskać więcej informacji, zobacz [tworzenie z wiersza polecenia](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) lub [wywoływanie kompilatora wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a>Do wykonania przy użyciu kompilacja warunkowa #CONST lub #define  
  
1.  Wpisz odpowiedniej instrukcji języka programowania, w górnej części pliku kodu źródłowego.  
  
    |Język|Instrukcja|Wynik|  
    |--------------|---------------|------------|  
    |**Visual Basic**|**#CONST śledzenia = true**|Umożliwia śledzenie|  
    ||**#CONST śledzenia = false**|Wyłącza śledzenie|  
    ||**#CONST debugowania = true**|Włącza debugowanie|  
    ||**#CONST debugowania = false**|Wyłącza debugowanie|  
    |**C#**|**#define śledzenia**|Umożliwia śledzenie|  
    ||**#undef śledzenia**|Wyłącza śledzenie|  
    ||**#define debugowania**|Włącza debugowanie|  
    ||**#undef debugowania**|Wyłącza debugowanie|  
  
### <a name="to-disable-tracing-or-debugging"></a>Aby wyłączyć śledzenia i debugowania  
  
1.  Usuń dyrektywy kompilatora w kodzie źródłowym.  
  
     \-lub -  
  
2.  Komentarz dyrektywy kompilatora.  
  
    > [!NOTE]
    >  Gdy wszystko będzie gotowe skompilować, można wybrać **kompilacji** z **kompilacji** menu, lub użyj metody wiersza polecenia, ale bez wpisywania **d:** do definiowania warunkowe symbole kompilacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie i Instrumentacja aplikacji](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [Porady: tworzenie, inicjowanie i konfigurowanie przełączników śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)  
 [Przełączniki śledzenia](../../../docs/framework/debug-trace-profile/trace-switches.md)  
 [Obiekty nasłuchujące śledzenia](../../../docs/framework/debug-trace-profile/trace-listeners.md)  
 [Porady: Dodawanie instrukcji śledzenia do kodu aplikacji](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)  
 [Porady: Ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)  
 [Porady: wywoływanie kompilatora wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)
