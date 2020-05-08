---
title: Koncepcje i model obiektów .NET Compiler Platform SDK
description: To omówienie zapewnia efektywność pracy z zestawem SDK kompilatora platformy .NET. Poznasz warstwy interfejsu API, typy główne i ogólny model obiektów.
ms.date: 10/10/2017
ms.custom: mvc
ms.openlocfilehash: 529ce6fbdef22964251c8b22abbd5d8aadab633d
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975943"
---
# <a name="understand-the-net-compiler-platform-sdk-model"></a>Poznaj model zestawu SDK .NET Compiler Platform

Kompilator przetwarza kod napisany przy użyciu reguł strukturalnych, które często różnią się od sposobu, w jaki ludzie czytają i wiedzą kod. Podstawowe informacje o modelu używanym przez kompilatory są niezbędne do poznania interfejsów API używanych podczas tworzenia narzędzi opartych na Roslyn.

## <a name="compiler-pipeline-functional-areas"></a>Obszary funkcjonalne potoku kompilatora

Zestaw .NET Compiler Platform SDK uwidacznia analizę kodu w języku C# i Visual Basic kompilatory jako konsumenta, dostarczając warstwę interfejsu API, która odzwierciedla tradycyjny potok kompilatora.

![kroki kompilatora przetwarzające kod źródłowy do kodu obiektu](media/compiler-api-model/compiler-pipeline.png)

Każda faza tego potoku jest osobnym składnikiem. Najpierw etap analizy tokenizes i analizuje tekst źródłowy do składni, która następuje po gramatyce języka. Druga faza deklaracji analizuje źródłowe i zaimportowane metadane do postaci nazwanych symboli. Następnie faza powiązania dopasowuje identyfikatory w kodzie do symboli. Na koniec etap emisji emituje zestaw ze wszystkimi informacjami skompilowanymi przez kompilator.

![Interfejs API potoku kompilatora zapewnia dostęp do każdego kroku, który jest częścią potoku kompilatora](media/compiler-api-model/compiler-pipeline-api.png)

Dla każdego z tych faz zestaw SDK .NET Compiler Platform uwidacznia model obiektów, który umożliwia dostęp do informacji w tej fazie. Etap analizy uwidacznia drzewo składni, ale faza deklaracji uwidacznia hierarchiczną tabelę symboli, faza powiązania ujawnia wynik analizy semantycznej kompilatora, a faza emisji jest interfejsem API, który tworzy kody bajtów IL.

![usługi językowe dostępne z interfejsu API kompilatora na każdym etapie potoku kompilatora](media/compiler-api-model/compiler-pipeline-lang-svc.png)

Każdy kompilator łączy te składniki razem z pojedynczym kompleksem.

Te interfejsy API są takie same, jak w programie Visual Studio. Na przykład funkcje tworzenia konspektu kodu i formatowania używają drzew składni, a funkcje Przeglądarka obiektów i nawigacji używają tabeli symboli, refaktoryzacji i przechodzenia do definicji używają modelu semantycznego, a Edycja i kontynuowanie korzysta ze wszystkich tych elementów, w tym interfejsu API emisji.

## <a name="api-layers"></a>Warstwy interfejsu API

Zestaw SDK kompilatora .NET składa się z dwóch głównych warstw interfejsów API: interfejsów API kompilatora i interfejsów API obszarów roboczych.

![warstwy interfejsu API reprezentowane przez interfejsy API potoku kompilatora](media/compiler-api-model/api-layers.png)

### <a name="compiler-apis"></a>Interfejsy API kompilatora

Warstwa kompilatora zawiera modele obiektów, które odnoszą się do informacji uwidocznionych w każdej fazie potoku kompilatora, składni i semantyki. Warstwa kompilatora zawiera również niemodyfikowalną migawkę pojedynczego wywołania kompilatora, w tym odwołania do zestawów, opcje kompilatora i pliki kodu źródłowego. Istnieją dwa różne interfejsy API, które reprezentują język C# i język Visual Basic. Te dwa interfejsy API są podobne do kształtu, ale są dostosowane do poszczególnych języków. Ta warstwa nie ma żadnych zależności w składnikach programu Visual Studio.

### <a name="diagnostic-apis"></a>Diagnostyczne interfejsy API

W ramach analizy kompilator może utworzyć zestaw danych diagnostycznych obejmujących wszystkie elementy składni, semantyki i błędy przypisania do różnych ostrzeżeń i diagnostyki informacyjnej. Warstwa interfejsu API kompilatora udostępnia diagnostykę za pomocą rozszerzalnego interfejsu API, który umożliwia przełączenie analizatorów zdefiniowanych przez użytkownika do procesu kompilacji. Umożliwia ona wytwarzanie przez użytkownika diagnostyki, takich jak te, które są tworzone przez narzędzia takie jak StyleCop lub FxCop, do wygenerowania w ramach diagnostyki zdefiniowanej przez kompilator. Zapewnianie diagnostyki w ten sposób pozwala na integrację naturalnie z narzędziami, takimi jak MSBuild i Visual Studio, które są zależne od diagnostyki dla takich środowisk, jak zatrzymanie kompilowania na podstawie zasad i wyświetlanie w edytorze i sugerowanie poprawek w kodzie.

### <a name="scripting-apis"></a>Interfejsy API obsługi skryptów

Interfejsy API hostingu i skryptów są częścią warstwy kompilatora. Można ich używać do wykonywania fragmentów kodu i gromadzenia kontekstu wykonywania środowiska uruchomieniowego.
W języku C# Interactive REPL (pętla odczytu-Szacuj-Print) używa tych interfejsów API. REPL umożliwia używanie języka C# w języku skryptowym, wykonywanie kodu w sposób interaktywny podczas pisania.

### <a name="workspaces-apis"></a>Interfejsy API obszarów roboczych

Warstwa obszary robocze zawiera interfejs API obszaru roboczego, który jest punktem wyjścia do przeprowadzania analizy kodu i refaktoryzacji całego rozwiązania. Pomaga to w organizowaniu wszystkich informacji o projektach w rozwiązaniu w jednym modelu obiektów, co zapewnia bezpośredni dostęp do modeli obiektów warstwy kompilatora bez potrzeby analizowania plików, konfigurowania opcji i zarządzania zależnościami między projektami.

Ponadto warstwa obszarów roboczych ma zestaw interfejsów API używanych podczas implementowania analizy kodu i narzędzi refaktoryzacji, które działają w środowisku hosta, takim jak środowisko IDE programu Visual Studio. Przykłady obejmują interfejsy API Znajdź wszystkie odwołania, formatowanie i generowanie kodu.

Ta warstwa nie ma żadnych zależności w składnikach programu Visual Studio.
