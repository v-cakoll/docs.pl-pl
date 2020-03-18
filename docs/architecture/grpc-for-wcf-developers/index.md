---
title: ASP.NET Core gRPC dla programistów WCF - gRPC dla programistów WCF
description: Wprowadzenie do budowania usług gRPC w ASP.NET Core 3.0 dla deweloperów WCF
ms.date: 09/02/2019
ms.openlocfilehash: 40307124c521659a00339884bacf48881fa3e048
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77543238"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a>Usługa gRPC platformy ASP.NET Core dla deweloperów WCF

![obraz okładki](./media/cover.png)

OPUBLIKOWANA PRZEZ

Zespoły produktów Microsoft Developer Division, .NET i Visual Studio

Oddział Firmy Microsoft Corporation

One Microsoft Way

Redmond (Waszyngton) 98052-6399

Prawa autorskie © 2019 przez Microsoft Corporation

Wszelkie prawa zastrzeżone. Żadna część treści tej książki nie może być powielana lub przekazywana w jakiejkolwiek formie lub w jakikolwiek sposób bez pisemnej zgody wydawcy.

Ta książka jest "tak jak jest" i wyraża poglądy i opinie autora. Poglądy, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odniesienia do stron internetowych, mogą ulec zmianie bez powiadomienia.

Niektóre z przykładów przedstawiono wyłącznie do celów informacyjnych i są one fikcyjne. Żadne rzeczywiste skojarzenia lub związki nie są zamierzone ani wnioskowane.

Microsoft i znaki towarowe https://www.microsoft.com wymienione na stronie internetowej "Znaki towarowe" są znakami towarowymi grupy firm Microsoft.

Logo wieloryba Docker jest zastrzeżonym znakiem towarowym firmy Docker, Inc. Używanym za zgodą.

Wszystkie inne znaki i logo są własnością ich właścicieli.

Autorów:

> **Mark Rendle** - Dyrektor Techniczny - [Visual Recode](https://visualrecode.com)
>
> **Miranda Steiner** - Autor techniczny

Edytor:

> **Maira Wenzel** - Sr. Content Developer - Microsoft

## <a name="introduction"></a>Wprowadzenie

gRPC to nowoczesne ramy budowania usług sieciowych i aplikacji rozproszonych. Wyobraź sobie wydajność powiązań NetTCP usługi Windows Communication Foundation (WCF) w połączeniu z współdziałaniem protokołu SOAP między platformami. gRPC opiera się na HTTP/2 i protobuf ie kodowania komunikatów, aby zapewnić wysoką wydajność, niską przepustowość komunikacji między aplikacjami i usługami. Obsługuje generowanie kodu serwera i klienta w najpopularniejszych językach i platformach programowania, w tym .NET, Java, Python, Node.js, Go i C++. Dzięki pierwszorzędnej obsłudze gRPC w ASP.NET Core 3.0, obok istniejących narzędzi i bibliotek gRPC dla .NET 4.x, jest to doskonała alternatywa dla WCF dla zespołów programistycznych, które chcą przyjąć .NET Core w swoich organizacjach.

## <a name="who-should-use-this-guide"></a>Kto powinien skorzystać z tego przewodnika

Ten przewodnik został napisany dla deweloperów pracujących w .NET Framework lub .NET Core, którzy wcześniej używali WCF i którzy chcą przeprowadzić migrację swoich aplikacji do nowoczesnego środowiska RPC dla .NET Core 3.0 i nowszych wersjach. Ogólnie rzecz biorąc, jeśli uaktualniasz lub rozważasz uaktualnienie do .NET Core 3.0 i chcesz użyć wbudowanych narzędzi gRPC, ten przewodnik jest również przydatny.

## <a name="how-you-can-use-this-guide"></a>Jak korzystać z tego przewodnika

Jest to krótkie wprowadzenie do tworzenia usług gRPC w ASP.NET Core 3.0, ze szczególnym odniesieniem do WCF jako analogicznej platformy. Wyjaśnia zasady gRPC, odnoszące się do każdej koncepcji do równoważnych funkcji WCF i oferuje wskazówki dotyczące migracji istniejącej aplikacji WCF do gRPC. Jest to również przydatne dla programistów, którzy mają doświadczenie z WCF i chcą nauczyć gRPC do tworzenia nowych usług. Przykładowe aplikacje można użyć jako szablon lub odwołanie do własnych projektów i można swobodnie kopiować i ponownie używać kodu z książki lub jej przykładów.

Nie krępuj się przekazać ten przewodnik do swojego zespołu, aby zapewnić wspólne zrozumienie tych rozważań i możliwości. Możliwość zapewnienia spójnego stosowania wzorców i praktyk architektonicznych przez wszystkich pracujących na podstawie wspólnego zestawu terminów i podstawowych zasad.

## <a name="references"></a>Dokumentacja

- **Witryna internetowa strony internetowej gRPC**
  <https://grpc.io>
- **Wybór między programami .NET Core a platformą .NET Framework dla aplikacji serwerowych**
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[Dalej](introduction.md)
