---
title: Zestaw SDK platformy kompilatora .NET pojęcia i model obiektów
description: W tym omówieniu przedstawiono tła, będzie potrzebne wydajnie pracować przy użyciu kompilatora .NET SDK. Dowiesz się warstwy interfejsu API, głównych typów zaangażowanych i ogólnym modelu obiektu.
ms.date: 10/10/2017
ms.custom: mvc
ms.openlocfilehash: ee8f902bf1df8b63e229fd518e7a0c592fcd47ca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706704"
---
# <a name="understand-the-net-compiler-platform-sdk-model"></a>Informacje o modelu zestawu SDK platformy kompilatora .NET

Kompilatory przetwarzać kod, który napiszesz następujące reguły ze strukturą, które często różnią się od ludzi sposób przeczytać i sprawdzić kod. Podstawową wiedzę na temat model wykorzystywany przez kompilatory jest niezbędne do zrozumienia interfejsów API, można użyć podczas tworzenia narzędzi opartych na programie Roslyn. 

## <a name="compiler-pipeline-functional-areas"></a>Obszarów funkcjonalnych potoku kompilatora

Udostępnia zestaw SDK platformy kompilatora .NET C# i Kompilatory języka Visual Basic code analizy dla Ciebie jako użytkownik, zapewniając warstwę interfejsu API, która odzwierciedla potoku tradycyjnych kompilatora.

![kroki przetwarzania kodu źródłowego z kodem obiektu potoku kompilatora](media/compiler-api-model/compiler-pipeline.png)

Każda faza ten potok jest składnikiem niezależnym. Najpierw faza analizy tokenizes i analizuje tekst źródłowy do składni, który następuje po gramatyki języka. Po drugie faza deklaracji analizuje źródła i importowane metadane do formularza, symbole. Następnie w fazie powiązania dopasowuje identyfikatorach w kodzie do symboli. Na koniec w fazie emitowanie emituje zestawu wszystkie informacje, które są tworzone przez kompilator.

![potok kompilatora interfejs api zapewnia dostęp do każdego kroku, który jest częścią potoku kompilatora](media/compiler-api-model/compiler-pipeline-api.png)

Odpowiadający każdej z tych faz, zestawu SDK platformy kompilatora .NET udostępnia model obiektowy, który umożliwia dostęp do informacji na tym etapie. Faza analizy przedstawia drzewo składni, faza deklaracji przedstawia tabelę hierarchiczną symbolu, w fazie powiązania przedstawia wynik analizy semantycznej kompilatora i faza emitowanie to interfejs API, który generuje kody bajt IL.

![dostępne z kompilatora usługi języka interfejsu api na każdym etapie potoku kompilatora](media/compiler-api-model/compiler-pipeline-lang-svc.png)

Każdy kompilator łączy w sobie te składniki ze sobą jako jednej całości end-to-end.

Te interfejsy API są takie same jak użyte przez program Visual Studio. Na przykład kodu, tworzenie konspektów i funkcji formatowania, używanie drzew składni, skorzystaj z tabeli symboli, refaktoryzacji, funkcji przeglądarki obiektów i nawigacji definicja polecenia przejdź do używania tego modelu semantycznego i Edytuj i Kontynuuj używa wszystkich z nich, w tym interfejs API emisji. 

## <a name="api-layers"></a>Warstwy interfejsu API

Kompilator platformy .NET, zestaw SDK składa się z dwóch głównych warstw interfejsów API: kompilatora interfejsów API i interfejsów API w obszarach roboczych.

![warstwy interfejsu api, reprezentowane przez kompilator potoku interfejsów API](media/compiler-api-model/api-layers.png)

### <a name="compiler-apis"></a>Interfejsy API kompilatora

Warstwa kompilatora zawiera modele obiektów, które odnoszą się do informacji uwidocznionych w każdej fazie potoku kompilatora, zarówno syntaktyczna i semantyczna. Warstwa kompilatora zawiera również niezmienne migawki na pojedyncze wywołanie kompilatora, w tym odwołania do zestawów, opcje kompilatora i pliki kodu źródłowego. Istnieją dwa różne interfejsy API reprezentujące C# języka i języka Visual Basic. Te dwa interfejsy API są podobne w kształcie, ale dostosowane do o wysokiej wierności do każdego z poszczególnych języków. Ta warstwa nie ma zależności na składniki programu Visual Studio.

### <a name="diagnostic-apis"></a>Interfejs API diagnostyki

Jako część ich analizy kompilator może zwrócić zestaw diagnostyki, obejmujące składnię i semantyczne i błędy asercję określonego przypisania do różnych ostrzeżenia i Diagnostyka informacyjne. Warstwa interfejsu API kompilatora udostępnia diagnostyki za pomocą rozszerzonego interfejsu API, umożliwiająca zdefiniowanych przez użytkownika analizatory być podłączony do procesu kompilacji. Umożliwia ona diagnostyki zdefiniowanych przez użytkownika, takich jak produkowanych przez narzędzia, takie jak StyleCop lub programu FxCop, opracowywane równolegle diagnostyki zdefiniowanego przez kompilator. Tworzenie diagnostyki w ten sposób ma tę zaletę, naturalny sposób integracji z narzędziami takimi jak MSBuild i Visual Studio, które są zależne od diagnostykę dla środowisk, takich jak zatrzymywanie kompilacji opartych na zasadach i wyświetlanie na żywo faliste linie w edytorze i sugerowanie kodu poprawki.

### <a name="scripting-apis"></a>Interfejsy API obsługi skryptów

Hosting i interfejsy API obsługi skryptów są częścią warstwy kompilatora. Używając ich wykonywania fragmenty kodu i grupowania kontekstu wykonania środowiska uruchomieniowego.
C# Interaktywna pętla REPL (odczytu oceny — Drukuj pętli) korzysta z tych interfejsów API. REPL pozwala na użycie C# jako języka skryptowego wykonywanie kodu interaktywnego podczas jej pisania.

### <a name="workspaces-apis"></a>Interfejsy API obszarów roboczych

Warstwa obszary robocze zawiera API obszaru roboczego, który jest punktem wyjścia do wykonywania analizy kodu i refaktoryzacji za pośrednictwem całego rozwiązania. Pomaga w organizowaniu wszystkie informacje dotyczące projektów w rozwiązaniu do pojedynczego obiektu modelu, oferując bezpośredni dostęp do modeli obiektów warstwy kompilatora bez konieczności analizować pliki, skonfiguruj opcje, lub zarządzanie zależnościami projektu do projektu .

Ponadto obszary robocze warstwy powierzchnie, zestaw interfejsów API używane podczas wykonywania analizy kodu i narzędzi, które działają w środowisku hosta refaktoryzacji, takie jak środowiska IDE programu Visual Studio. Przykłady obejmują Znajdź wszystkie odwołania, formatowanie i interfejsy API generowania kodu.

Ta warstwa nie ma zależności na składniki programu Visual Studio.
