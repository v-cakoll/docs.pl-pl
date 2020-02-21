---
title: ASP.NET Core gRPC for WCF Developers — gRPC dla deweloperów WCF
description: Wprowadzenie do tworzenia usług gRPC w ASP.NET Core 3,0 dla deweloperów WCF
ms.date: 09/02/2019
ms.openlocfilehash: 40307124c521659a00339884bacf48881fa3e048
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543238"
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

Autorzy:

> **Mark The Rendle** -dyrektor ds. technicznych — [Visual firmy Recode](https://visualrecode.com)
>
> **Miranda Steiner** — autor techniczny

Edytor

> **Maira Wenzel** — SR. Content Developer — Microsoft

## <a name="introduction"></a>Wprowadzenie

gRPC to nowoczesne środowisko do tworzenia usług sieciowych i aplikacji rozproszonych. Wyobraź sobie Windows Communication Foundation wydajność powiązań NetTCP (WCF) w połączeniu z międzyplatformowym współdziałaniem protokołu SOAP. gRPC kompiluje na HTTP/2 i protokół kodowania komunikatów protobuf, aby zapewnić wysoką wydajność, komunikację o niskiej przepustowości między aplikacjami i usługami. Obsługuje ona generowanie kodu serwera i klienta w większości popularnych języków programowania i platform, w tym .NET, Java, Python, Node. js, go i C++. Dzięki pierwszej klasie wsparcia dla gRPC w ASP.NET Core 3,0 wraz z istniejącymi narzędziami i bibliotekami gRPC dla platformy .NET 4. x jest to świetna alternatywa dla usług WCF dla zespołów programistycznych, które chcą przyjąć platformę .NET Core w swoich organizacjach.

## <a name="who-should-use-this-guide"></a>Kto powinien korzystać z tego przewodnika

Ten przewodnik został utworzony dla deweloperów pracujących w .NET Framework lub .NET Core, którzy wcześniej korzystali z usług WCF, i którzy chcą migrować swoje aplikacje do nowoczesnego środowiska RPC dla programu .NET Core 3,0 i jego nowszych wersji. Ogólnie rzecz biorąc, Jeśli uaktualniasz lub rozważasz uaktualnienie do programu .NET Core 3,0 i chcesz korzystać z wbudowanych narzędzi gRPC, ten przewodnik jest również przydatny.

## <a name="how-you-can-use-this-guide"></a>Jak można użyć tego przewodnika

Jest to krótkie wprowadzenie do tworzenia usług gRPC w ASP.NET Core 3,0, z uwzględnieniem programu WCF jako analogicznej platformy. Wyjaśniono zasady gRPC, odnoszące się do poszczególnych koncepcji funkcji WCF i oferuje wskazówki dotyczące migrowania istniejącej aplikacji WCF do gRPC. Jest on również przydatny dla deweloperów, którzy korzystają z WCF i chcą uczyć się gRPC w tworzeniu nowych usług. Przykładowymi aplikacjami można używać jako szablonu lub odwołania do własnych projektów i możesz kopiować i ponownie używać kodu z książki lub jej przykładów.

Możesz przesłać dalej ten przewodnik do zespołu, aby pomóc w zapewnieniu powszechnej wiedzy na temat tych zagadnień i możliwości. Korzystanie ze wspólnego zestawu warunków i podstawowych zasad ułatwia zapewnienie spójnego stosowania wzorców i praktyk architektury.

## <a name="references"></a>Dokumentacja

- 
  **witryny sieci Web gRPC** <https://grpc.io>
- **Wybieranie między programami .NET Core i .NET Framework dla aplikacji serwerowych**
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[Dalej](introduction.md)
