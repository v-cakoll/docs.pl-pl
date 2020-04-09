---
title: ASP.NET Core gRPC dla programistów WCF - gRPC dla programistów WCF
description: Wprowadzenie do tworzenia usług gRPC w ASP.NET Core 3.0 dla programistów WCF
ms.date: 09/02/2019
ms.openlocfilehash: 175dfbf1880a0937615543c248fba3bed0e25c23
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988963"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a>Usługa gRPC platformy ASP.NET Core dla deweloperów WCF

![obraz okładki](./media/cover.png)

OPUBLIKOWANA PRZEZ

Zespoły produktów Microsoft Developer Division, .NET i Visual Studio

Oddział firmy Microsoft Corporation

One Microsoft Way

Redmond, Waszyngton 98052-6399

Prawa autorskie © 2019 przez Microsoft Corporation

Wszelkie prawa zastrzeżone. Żadna część zawartości tej książki nie może być powielana ani przekazywana w jakiejkolwiek formie lub w jakikolwiek sposób bez pisemnej zgody wydawcy.

Książka ta jest dostarczana "tak jak jest" i wyraża poglądy i opinie autora. Poglądy, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odniesienia do stron internetowych, mogą ulec zmianie bez powiadomienia.

Niektóre z przykładów przedstawiono wyłącznie do celów informacyjnych i są one fikcyjne. Żadne rzeczywiste skojarzenia lub związki nie są zamierzone ani wnioskowane.

Firma Microsoft i znaki https://www.microsoft.com towarowe wymienione na stronie internetowej "Znaki towarowe" są znakami towarowymi grupy firm Microsoft.

Logo docker wielorybów jest zastrzeżonym znakiem towarowym firmy Docker, Inc. Używany za zgodą.

Wszystkie inne znaki i logo są własnością ich odpowiednich właścicieli.

Autorów:

> **Mark Rendle** - Dyrektor Techniczny - [Visual Recode](https://visualrecode.com)
>
> **Miranda Steiner** - autor techniczny

Edytor:

> **Maira Wenzel** - Sr. Content Developer - Microsoft

## <a name="introduction"></a>Wprowadzenie

gRPC to nowoczesne ramy dla tworzenia usług sieciowych i aplikacji rozproszonych. Wyobraź sobie wydajność powiązań NetTCP programu Windows Communication Foundation (WCF) w połączeniu z interoperacyjnością protokołu SOAP na wielu platformach. GRPC opiera się na HTTP/2 i protobuf message-encoding protocol, aby zapewnić wysoką wydajność, niską przepustowość komunikacji między aplikacjami i usługami. Obsługuje generowanie kodu serwera i klienta w najpopularniejszych językach programowania i platformach, w tym .NET, Java, Python, Node.js, Go i C++. Dzięki najwyższej klasy obsłudze gRPC w ASP.NET Core 3.0, obok istniejących narzędzi i bibliotek gRPC dla platformy .NET 4.x, jest to doskonała alternatywa dla WCF dla zespołów programistycznych, które chcą przyjąć .NET Core w swoich organizacjach.

## <a name="who-should-use-this-guide"></a>Kto powinien korzystać z tego przewodnika

Ten przewodnik został napisany dla deweloperów pracujących w programie .NET Framework lub .NET Core, którzy wcześniej używali WCF i którzy chcą przeprowadzić migrację swoich aplikacji do nowoczesnego środowiska RPC dla platformy .NET Core 3.0 i nowszych wersji. Ogólniej rzecz biorąc, jeśli uaktualniasz lub rozważasz uaktualnienie do platformy .NET Core 3.0 i chcesz użyć wbudowanych narzędzi gRPC, ten przewodnik jest również przydatny.

## <a name="how-you-can-use-this-guide"></a>Jak można korzystać z tego przewodnika

Jest to krótkie wprowadzenie do tworzenia usług gRPC w ASP.NET Core 3.0, ze szczególnym uwzględnieniem WCF jako analogicznej platformy. Wyjaśniono w nim zasady gRPC, odnoszące się do każdej koncepcji z równoważnymi cechami WCF, i oferuje wskazówki dotyczące migracji istniejącej aplikacji WCF do gRPC. Jest to również przydatne dla programistów, którzy mają doświadczenie z WCF i chcą nauczyć się gRPC do tworzenia nowych usług. Przykładowe aplikacje można używać jako szablonu lub odwołania dla własnych projektów i można kopiować i ponownie używać kodu z książki lub jej przykładów.

Możesz przesłać ten przewodnik do swojego zespołu, aby zapewnić wspólne zrozumienie tych zagadnień i możliwości. Posiadanie wszystkich pracujących ze wspólnego zestawu terminów i podstawowych zasad pomaga zapewnić spójne stosowanie wzorców i praktyk architektonicznych.

## <a name="references"></a>Dokumentacja

- **Witryna internetowa firmy gRPC**
  <https://grpc.io>
- **Wybór między programem .NET Core a platformą .NET Framework dla aplikacji serwerowych**
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[Dalej](introduction.md)
