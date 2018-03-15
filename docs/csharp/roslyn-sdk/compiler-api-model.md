---
title: "Zestaw SDK platformy kompilatora .NET pojęcia i model obiektów"
description: "Ten przegląd zawiera tło, musisz działał efektywnie przez kompilator .NET SDK. Dowiesz się warstwy interfejsu API, główne typy i ogólny model obiektów."
author: billwagner
ms.author: wiwagn
ms.date: 10/10/2017
ms.topic: conceptual
ms.prod: .net
ms.devlang: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: d230d334eba4e438635a4c70e8c1b5fc5075b065
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="understand-the-net-compiler-platform-sdk-model"></a>Zrozumienie modelu zestawu SDK platformy kompilatora .NET

Kompilatory przetworzyć tworzonego następujące reguły strukturalnych, które często różnią się od ludzi sposób przeczytane i zrozumiane kodu kodu. Podstawową wiedzę na temat modelu używanego przez kompilatory jest niezbędne do zrozumienia interfejsów API, można użyć podczas tworzenia narzędzia oparte na Roslyn. 

## <a name="compiler-pipeline-functional-areas"></a>Obszarów funkcjonalnych potoku kompilatora

Zestawu SDK platformy kompilatora .NET przedstawia Kompilatory języka C# i Visual Basic analizy kodu dla Ciebie klientów przez zapewnienie warstwę interfejsu API, która odzwierciedla potoku tradycyjnych kompilatora.

![kroki przetwarzania kodu źródłowego z kodem obiektu potoku kompilatora](media/compiler-pipeline.png)

Każdej fazy tego potoku jest inny składnik. Po pierwsze faza analizy tokenizes i przeanalizowany tekst źródłowy do składni stosowanej gramatyki języka. Po drugie faza deklaracji analizuje źródła i importowane metadane do formularza symbole. Następnie fazie wiązania odpowiada identyfikatorów w kodzie do symboli. Na koniec fazy emitowanie emituje zestawu wszystkie informacje, które są tworzone przez kompilator.

![potok kompilatora interfejsu api zapewnia dostęp do każdego kroku, który jest częścią pipelien kompilatora](media/compiler-pipeline-api.png)

Odpowiadający każdej z tych faz, zestawu SDK platformy kompilatora .NET przedstawia model obiektów, która zezwala na dostęp do informacji w tej fazie. Faza analizy przedstawia drzewa składni, faza deklaracji przedstawia tabelę hierarchiczną symbol fazie wiązania przedstawia wynik analizy semantycznego kompilatora i faza emitowanie to interfejs API, który spowoduje utworzenie kodów bajtów IL.

![dostępne z kompilatora języka usługi interfejsu api w każdym kroku procesu kompilatora](media/compiler-pipeline-lang-svc.png)

Każdy kompilatora łączy te składniki ze sobą jednej całości end-to-end.

Te interfejsy API są takie same jak używane przez program Visual Studio. Dla wystąpienia kodu zwijania i funkcje formatowania używanie drzew składni, tabeli symboli refaktoryzacje Użyj funkcji przeglądarki obiektów i nawigacji przejdź do definicji Użyj modelu semantycznego i Edytuj i Kontynuuj wykorzystuje wszystkie z nich, łącznie z interfejsu API emisji. 

## <a name="api-layers"></a>Warstwy interfejsu API

Kompilator .NET SDK składa się z dwóch warstw głównego interfejsów API: kompilatora interfejsów API i interfejsów API obszarów roboczych.

![warstwy interfejsu api reprezentowany przez kompilator interfejsów API potoku](media/api-layers.png)

### <a name="compiler-apis"></a>Interfejsy API kompilatora

Warstwa kompilatora zawiera modeli obiektów, które odpowiadają informacje udostępniane w poszczególnych fazach potoku kompilatora, zarówno składni i semantycznego. Warstwa kompilatora zawiera również niezmienne migawki jednego wywołania kompilatora, w tym odwołania do zestawów, opcje kompilatora i plików kodu źródłowego. Istnieją dwa różne interfejsów API, które reprezentują języka C# i języka Visual Basic. Te dwa interfejsy API są podobne w kształcie, ale dostosowane do o wysokiej wierności dla każdego języka indywidualnych. Ta warstwa nie ma zależności na składnikach programu Visual Studio.

### <a name="diagnostic-apis"></a>Interfejsy API diagnostycznych

W ramach swojej analizy kompilator może utworzyć zestaw diagnostyki obejmujące wszystkie elementy z składnię semantyczne i błędy określoną przypisania do różnych ostrzeżenia i informacyjną diagnostyki. Warstwę interfejsu API kompilatora przedstawia Diagnostyka za pośrednictwem rozszerzonego interfejsu API, umożliwiający użytkownika analizatorów być podłączony do procesu kompilacji. Umożliwia on diagnostics zdefiniowane przez użytkownika, takich jak te utworzone przez narzędzia, takie jak StyleCop lub programu FxCop, do wyprodukowania obok zdefiniowane przez kompilator diagnostyki. Tworzenie diagnostyki w ten sposób ma korzyści integracji naturalny z narzędzi, takich jak program MSBuild i Visual Studio, które są zależne od diagnostyki dla środowiska, takie jak zatrzymywanie kompilacji na podstawie zasad i przedstawiający zygzaki na żywo w edytorze i sugerowanie kodu poprawki.

### <a name="scripting-apis"></a>Interfejsy API obsługi skryptów

Hosting i skryptów interfejsy API są częścią warstwy kompilatora. Można używać ich do wykonywania fragmentów kodu i grupowania kontekstu wykonywania środowiska uruchomieniowego.
C# interaktywny REPL (odczyt oceny-Drukuj pętli) korzysta z poniższych interfejsów API. REPL pozwala na użycie C# jako język skryptów, wykonywanie kodu interaktywnego pisania go.

### <a name="workspaces-apis"></a>Interfejsy API obszary robocze

Warstwa obszarów roboczych zawiera interfejsu API obszaru roboczego, który jest punkt początkowy podczas analizy kodu i refaktoryzacji za pośrednictwem całego rozwiązania. Ułatwia organizowanie wszystkie informacje dotyczące projektów w rozwiązaniu do pojedynczego obiektu modelu, oferty bezpośredni dostęp do modeli obiektów warstwy kompilatora bez konieczności analizy plików, skonfiguruj opcje, lub zarządzania zależności projektu do projektu .

Ponadto obszary robocze warstwy powierzchni zestaw interfejsów API używane podczas wykonywania analizy kodu oraz refaktoryzacji narzędzia, które działają w środowisku hosta, takich jak środowiska IDE programu Visual Studio. Przykładami Znajdź wszystkie odwołania, formatowanie i interfejsy API generowania kodu.

Ta warstwa nie ma zależności na składnikach programu Visual Studio.
