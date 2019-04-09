---
title: 'Instrukcje: Kompilowanie warunkowe ze śledzeniem i debugowaniem'
ms.date: 03/30/2017
helpviewer_keywords:
- trace compiler options
- trace statements
- compiling source code, trace statements
- tracing [.NET Framework], enabling or disabling
- tracing [.NET Framework], compiling conditionally
- TRACE directive
- conditional compilation, tracing code
ms.assetid: 56d051c3-012c-42c1-9a58-7270edc624aa
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 76e442536e4c863031072adfb4d8716ca7a19aff
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158661"
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a>Instrukcje: Kompilowanie warunkowe ze śledzeniem i debugowaniem
Podczas debugowania aplikacji podczas tworzenia usługi śledzenia i dane wyjściowe debugowania przejdź do okna danych wyjściowych w programie Visual Studio. Jednak aby włączyć funkcje śledzenia do wdrożonej aplikacji, należy skompilować instrumentowanej aplikacji przy użyciu **śledzenia** dyrektywy kompilatora włączone. Dzięki temu kod śledzenia jest kompilowana do wersji aplikacji. Jeśli nie włączysz **śledzenia** dyrektywy, cały kod śledzenia jest ignorowany podczas kompilacji, a nie znajduje się w kodzie pliku wykonywalnego, który zostanie wdrożony.  
  
 Śledzenie i profilowanie metody skojarzony atrybuty warunkowe. Na przykład, jeśli warunkową atrybutu dla śledzenia jest **true**, wszystkie instrukcje śledzenia znajdują się w obrębie zestawu (plik skompilowanych .exe lub .dll); Jeśli **śledzenia** atrybut conditional jest **false**, instrukcji śledzenia nie są uwzględniane.  
  
 Może mieć **śledzenia** lub **debugowania** atrybut conditional włączona dla kompilacji, lub obie lub nie. Dlatego istnieją cztery typy kompilacji: **Debugowanie**, **śledzenia**, obie lub nie. Niektóre kompilacji wydania wdrożenia produkcyjnego może zawierać żadnego z tych celów; najbardziej debugujące kompilacje zawierać równocześnie.  
  
 Można określić ustawienia kompilatora dla aplikacji na kilka sposobów:  
  
-   Strony właściwości  
  
-   W wierszu polecenia  
  
-   **#CONST** (dla języka Visual Basic) i **#define** (dla C#)  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a>Aby zmienić ustawienia kompilacji z okna dialogowego strony właściwości  
  
1.  Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań**.  
  
2.  Wybierz **właściwości** z menu skrótów.  
  
    -   W języku Visual Basic, kliknij przycisk **skompilować** w lewym okienku na stronie właściwości, a następnie kliknij **zaawansowane opcje kompilacji** przycisk, aby wyświetlić **Zaawansowane ustawienia kompilatora**okno dialogowe. Zaznacz pole wyboru, jeśli dla ustawienia kompilatora, który chcesz włączyć. Wyczyść pola wyboru dla ustawień, które chcesz wyłączyć.  
  
    -   W C#, kliknij przycisk **kompilacji** tabulator w lewym okienku na stronie właściwości, a następnie zaznacz pole wyboru, aby włączyć ustawienia kompilatora. Wyczyść pola wyboru dla ustawień, które chcesz wyłączyć.  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a>Aby skompilować kod instrumentowanych przy użyciu wiersza polecenia  
  
1.  Ustaw przełącznik warunkowe kompilatora w wierszu polecenia. Kompilator będzie zawierać śledzenia lub możliwe jest debugowanie kodu w pliku wykonywalnym.  
  
     Na przykład następująca instrukcja kompilatora wprowadzone w wierszu polecenia zawierałoby kod śledzenia w skompilowany plik wykonywalny:  
  
     Dla języka Visual Basic: **vbc — r:System.dll -d: ŚLEDZENIE = TRUE -d: DEBUG = FALSE MyApplication.vb**  
  
     Aby uzyskać C#: **csc — r:System.dll -d: śledzenia -d: DEBUG = FALSE MyApplication.cs**  
  
    > [!TIP]
    >  Aby skompilować więcej niż jeden plik w aplikacji, pozostaw puste miejsce między nazwy plików, na przykład **MyApplication1.vb MyApplication2.vb MyApplication3.vb** lub **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.  
  
     Znaczenie dyrektywy kompilacji warunkowej używanych w powyższych przykładach jest następujące:  
  
    |— Dyrektywa|Znaczenie|  
    |---------------|-------------|  
    |`vbc`|kompilator Visual Basic|  
    |`csc`|C#Kompilator|  
    |`-r:`|Odwołuje się do zestawu zewnętrznego (EXE lub DLL)|  
    |`-d:`|Definiuje symbol kompilacji warunkowej|  
  
    > [!NOTE]
    >  Należy pisowni śledzenia i debugowania przy użyciu wielkich liter. Aby uzyskać więcej informacji na temat poleceń kompilacji warunkowej, wprowadź `vbc /?` (dla języka Visual Basic) lub `csc /?` (dla C#) w wierszu polecenia. Aby uzyskać więcej informacji, zobacz [tworzenie z wiersza polecenia](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) lub [wywoływanie kompilatora wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a>Do wykonania kompilacji warunkowej przy użyciu #CONST lub #define  
  
1.  Wpisz odpowiedniej instrukcji dla języka programowania, w górnej części pliku kodu źródłowego.  
  
    |Język|Instrukcja|Wynik|  
    |--------------|---------------|------------|  
    |**Visual Basic**|**# ŚLEDZENIA CONST = true**|Umożliwia włączenie śledzenia|  
    ||**# ŚLEDZENIA CONST = false**|Wyłącza śledzenie|  
    ||**#CONST debugowania = true**|Włącza debugowanie|  
    ||**#CONST debugowania = false**|Wyłącza debugowanie|  
    |**C#**|**#define śledzenia**|Umożliwia włączenie śledzenia|  
    ||**#undef śledzenia**|Wyłącza śledzenie|  
    ||**#define debugowania**|Włącza debugowanie|  
    ||**#undef debugowania**|Wyłącza debugowanie|  
  
### <a name="to-disable-tracing-or-debugging"></a>Aby wyłączyć śledzenia i debugowania  
  
Usuń dyrektywy kompilatora z kodu źródłowego.  
  
\- lub —  
  
Dyrektywy kompilatora w komentarz.  
  
> [!NOTE]
>  Gdy wszystko jest gotowe do kompilowania, możesz wybrać **kompilacji** z **kompilacji** menu lub użyć metody wiersza polecenia, ale bez wpisywania **d:** do definiowania warunkowe symbole kompilacji.  
  
## <a name="see-also"></a>Zobacz także

- [Śledzenie i instrumentacja aplikacji](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [Instrukcje: Tworzenie, inicjowanie i konfigurowanie przełączników śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)
- [Przełączniki śledzenia](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [Obiekty nasłuchujące śledzenia](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [Instrukcje: Dodawanie instrukcji śledzenia do kodu aplikacji](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [Instrukcje: ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [Instrukcje: Wywoływanie kompilatora wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)
