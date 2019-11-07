---
title: ASP.NET Core gRPC for WCF Developers — gRPC dla deweloperów WCF
description: Wprowadzenie do tworzenia usług gRPC w ASP.NET Core 3,0 dla deweloperów WCF
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: b89f5974dd18e7005c6479c5b9eead039364e654
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738073"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a>Usługa gRPC platformy ASP.NET Core dla deweloperów WCF

![obraz okładki](./media/cover.png)

OPUBLIKOWANO PRZEZ

Zespoły deweloperów firmy Microsoft, .NET i Visual Studio

Dział firmy Microsoft Corporation

One Microsoft Way

Redmond, Waszyngton 98052-6399

Prawa autorskie © 2019 przez firmę Microsoft Corporation

Wszelkie prawa zastrzeżone. Żadna część zawartości tej księgi nie może być odtwarzana ani przekazywana w żadnej formie ani za pomocą jakichkolwiek środków bez zgody na wydawcę.

Ta książka jest świadczona w postaci "AS-IS" i zawiera widoki i opinie autora. Widoki, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odwołania do witryn internetowych, mogą ulec zmianie bez powiadomienia.

Niektóre przykłady opisane w niniejszym dokumencie są dostępne tylko dla ilustracji i są fikcyjne. Żadne prawdziwe skojarzenie lub połączenie nie jest zamierzone ani nie powinno zostać wywnioskowane.

Firma Microsoft i znaki towarowe wymienione w https://www.microsoft.com na stronie "znaki towarowe" są znakami towarowymi grupy firm Microsoft.

Logo Docker Whale jest zastrzeżonym znakiem towarowym platformy Docker, Inc. używanym przez uprawnienie.

Wszystkie inne znaczniki i logo są własnością odpowiednich właścicieli.

Tworzone

> **Mark The Rendle** -dyrektor ds. technicznych — [Visual firmy Recode](https://visualrecode.com)
>
> **Miranda Steiner** — autor techniczny

Edytory

> **Maira Wenzel** — deweloper zawartości SR — Microsoft

## <a name="introduction"></a>Wprowadzenie

gRPC to nowoczesne środowisko do tworzenia usług sieciowych i aplikacji rozproszonych. Wyobraź sobie wydajność powiązań NetTCP w programie WCF dzięki międzyplatformowej współdziałaniu protokołu SOAP. gRPC kompiluje na HTTP/2 i protokół kodowania komunikatów protobuf, aby zapewnić wysoką wydajność, komunikację o niskiej przepustowości między aplikacjami i usługami. Obsługuje ona generowanie kodu serwera i klienta w większości popularnych języków programowania i platform, w tym .NET, Java, Python, Node. js, go C++ i innych. Dzięki pierwszej klasie obsługi gRPC w ASP.NET Core 3,0 wraz z istniejącymi narzędziami i bibliotekami gRPC dla platformy .NET 4. x uważamy, że jest to znakomita alternatywa dla usługi WCF dla zespołów programistycznych, które chcą przyjąć platformę .NET Core w swoich organizacjach.

## <a name="who-should-use-this-guide"></a>Kto powinien korzystać z tego przewodnika

Ten przewodnik został utworzony dla deweloperów pracujących w .NET Framework lub .NET Core, którzy wcześniej korzystali z usług WCF i chcący migrować swoje aplikacje do nowoczesnego środowiska RPC dla programu .NET Core 3,0 i jego nowszych wersji. Przewodnik może być również bardziej używany w przypadku deweloperów uaktualniających lub rozważających uaktualnienie do programu .NET Core 3,0, którzy chcą korzystać z wbudowanych narzędzi gRPC.

## <a name="how-you-can-use-this-guide"></a>Jak można użyć tego przewodnika

Jest to krótkie wprowadzenie do tworzenia usług gRPC w ASP.NET Core 3,0 z konkretnym odwołaniem do programu WCF jako analogicznej platformy. Wyjaśniono zasady gRPC, odnoszące się do poszczególnych koncepcji funkcji WCF i oferuje wskazówki dotyczące migrowania istniejącej aplikacji WCF do gRPC. Jest on również przydatny dla deweloperów, którzy korzystają z programu WCF i poszukują gRPC w tworzeniu nowych usług. Przykładowe aplikacje mogą służyć jako szablon lub odwołanie do własnych projektów, a ty możesz kopiować i ponownie używać kodu z książki lub jej przykładów.

Możesz przesłać dalej ten przewodnik do zespołu, aby pomóc w zapewnieniu powszechnej wiedzy na temat tych zagadnień i możliwości. Korzystanie ze wspólnego zestawu terminologii i podstawowych zasad pomaga zapewnić spójne stosowanie wzorców i praktyk architektury.

## <a name="references"></a>Odwołania

- **Witryna sieci Web gRPC**  
  <https://grpc.io>
- **Wybieranie między programami .NET Core i .NET Framework na potrzeby aplikacji serwerowych**  
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[Next](introduction.md)
