---
title: Pojęcia sdk platformy kompilatora .NET i model obiektu
description: Ten przegląd zapewnia tło, które należy skutecznie pracować z zestawem SDK kompilatora .NET. Dowiesz się warstwy interfejsu API, główne typy zaangażowanych i ogólny model obiektów.
ms.date: 10/10/2017
ms.custom: mvc
ms.openlocfilehash: e563260e21fb8807017db90ff63e30fec0415a48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156964"
---
# <a name="understand-the-net-compiler-platform-sdk-model"></a>Opis modelu sdk platformy kompilatora .NET

Kompilatory przetwarzają kod, który piszesz, zgodnie z regułami strukturalnymi, które często różnią się od sposobu, w jaki ludzie czytają i rozumieją kod. Podstawowa wiedza na temat modelu używanego przez kompilatory jest niezbędna do zrozumienia interfejsów API używanych podczas tworzenia narzędzi opartych na Roslyn.

## <a name="compiler-pipeline-functional-areas"></a>Obszary funkcjonalne potoku kompilatora

Zestaw SDK platformy kompilatora .NET udostępnia analizę kodu kompilatora C# i Visual Basic jako konsumenta, udostępniając warstwę interfejsu API, która odzwierciedla tradycyjny potok kompilatora.

![kroki przetwarzania kodu źródłowego potoku kompilatora do kodu obiektu](media/compiler-api-model/compiler-pipeline.png)

Każda faza tego potoku jest oddzielnym składnikiem. Po pierwsze, analiza fazy tokenizes i analizuje tekst źródłowy do składni, która następuje gramatyki językowej. Po drugie faza deklaracji analizuje źródło i importowane metadane w celu utworzenia nazwanych symboli. Następnie faza powiązania dopasowuje identyfikatory w kodzie do symboli. Na koniec fazy emituj emituje zestaw ze wszystkimi informacjami utworzonymi przez kompilator.

![interfejs api potoku kompilatora zapewnia dostęp do każdego kroku, który jest częścią potoku kompilatora](media/compiler-api-model/compiler-pipeline-api.png)

Odpowiadająca każdej z tych faz zestaw SDK platformy kompilatora .NET udostępnia model obiektu, który umożliwia dostęp do informacji na tej fazie. Faza analizy udostępnia drzewo składni, faza deklaracji udostępnia hierarchiczną tabelę symboli, faza wiązania udostępnia wynik analizy semantycznej kompilatora, a faza emitowania jest interfejsem API, który tworzy kody bajtów IL.

![usługi językowe dostępne z interfejsu api kompilatora na każdym etapie potoku kompilatora](media/compiler-api-model/compiler-pipeline-lang-svc.png)

Każdy kompilator łączy te składniki razem jako pojedynczą całość end-to-end.

Te interfejsy API są te same używane przez program Visual Studio. Na przykład funkcje konspektu i formatowania kodu używają drzew składni, przeglądarka obiektów i funkcje nawigacji używają tabeli symboli, refaktoryzacji i przejdź do definicji, a model semantyczny i Edit i Continue używają wszystkich tych elementów, w tym interfejsu API emitowania.

## <a name="api-layers"></a>Warstwy interfejsu API

Zestaw SDK kompilatora .NET składa się z dwóch głównych warstw interfejsów API: interfejsów API kompilatora i interfejsów API obszarów roboczych.

![warstwy interfejsu api reprezentowane przez potok kompilatora apis](media/compiler-api-model/api-layers.png)

### <a name="compiler-apis"></a>Interfejsy API kompilatora

Warstwa kompilatora zawiera modele obiektów, które odpowiadają informacji uwyponych w każdej fazie potoku kompilatora, zarówno składnii i semantyczne. Warstwa kompilatora zawiera również niezmienną migawkę pojedynczego wywołania kompilatora, w tym odwołań do zestawu, opcji kompilatora i plików kodu źródłowego. Istnieją dwa różne interfejsy API, które reprezentują język Języka C# i języka Języka Visual Basic. Te dwa interfejsy API mają podobny kształt, ale dostosowane do wysokiej wierności do każdego języka. Ta warstwa nie ma zależności od składników programu Visual Studio.

### <a name="diagnostic-apis"></a>Interfejsy API diagnostyki

W ramach analizy kompilator może wygenerować zestaw diagnostyki obejmujących wszystko, od składni, semantyczne i określone błędy przypisania do różnych ostrzeżeń i diagnostyki informacyjnej. Warstwa interfejsu API kompilatora udostępnia diagnostyki za pośrednictwem rozszerzalnego interfejsu API, który umożliwia analizatory zdefiniowane przez użytkownika, które mają być podłączone do procesu kompilacji. Umożliwia diagnostyki zdefiniowaneprzez użytkownika, takich jak te produkowane przez narzędzia, takie jak StyleCop lub FxCop, które mają być produkowane obok diagnostyki zdefiniowanej przez kompilator. Tworzenie diagnostyki w ten sposób ma tę zaletę integracji naturalnie z narzędziami, takimi jak MSBuild i Visual Studio, które zależą od diagnostyki dla doświadczeń, takich jak zatrzymanie kompilacji opartej na zasadach i wyświetlanie squiggles na żywo w edytorze i sugerowanie kodu Poprawki.

### <a name="scripting-apis"></a>Interfejsy API skryptów

Interfejsy API hostingu i skryptów są częścią warstwy kompilatora. Można ich używać do wykonywania fragmentów kodu i gromadzenia kontekstu wykonywania w czasie wykonywania.
C# interaktywne REPL (Odczyt-Ocena-Print Loop) używa tych interfejsów API. REPL umożliwia używanie języka C# jako języka skryptów, interakcyjnie wykonując kod podczas pisania.

### <a name="workspaces-apis"></a>Interfejsy API obszarów roboczych

Warstwa Obszary robocze zawiera interfejs API obszaru roboczego, który jest punktem wyjścia do analizy kodu i refaktoryzacji w całych rozwiązaniach. Pomaga w organizowaniu wszystkich informacji o projektach w rozwiązaniu w model jednego obiektu, oferując bezpośredni dostęp do modeli obiektów warstwy kompilatora bez konieczności analizowania plików, konfigurowania opcji lub zarządzania zależnościami projektu do projektu .

Ponadto warstwy workspaces powierzchnizestaw interfejsów API używane podczas implementowania analizy kodu i refaktoryzacji narzędzi, które działają w środowisku hosta, takich jak Visual Studio IDE. Przykłady obejmują znajdź wszystkie odwołania, formatowanie i interfejsy API generowania kodu.

Ta warstwa nie ma zależności od składników programu Visual Studio.
