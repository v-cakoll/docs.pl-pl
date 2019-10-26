---
title: ASP.NET Core gRPC for WCF Developers — gRPC dla deweloperów WCF
description: DO ZAPISANIA
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 6a5b4f6d0b47a272f7a753e22bfd61b06202944a
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919377"
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

CZYNNOŚĆ

## <a name="purpose"></a>Cel

CZYNNOŚĆ

## <a name="who-should-use-this-guide"></a>Kto powinien korzystać z tego przewodnika

**ZAKTUALIZUJ TEN**

Odbiorcy tego przewodnika są deweloperzy WCF, potencjalni klienci programistyczni i architektzy zainteresowani migrowaniem rozwiązań WCF w .NET Framework 4 i wcześniejszych, aby ASP.NET Core 3,0 przy użyciu usług gRPC Services.

## <a name="how-you-can-use-this-guide"></a>Jak można użyć tego przewodnika

**ZAKTUALIZUJ TEN**

Jest to krótkie wprowadzenie do tworzenia usług gRPC w ASP.NET Core 3,0 z konkretnym odwołaniem do programu WCF jako analogicznej platformy. Wyjaśniono zasady gRPC, odnoszące się do poszczególnych koncepcji funkcji WCF i oferuje wskazówki dotyczące migrowania istniejącej aplikacji WCF do gRPC. Jest on również przydatny dla deweloperów, którzy korzystają z programu WCF i poszukują gRPC w tworzeniu nowych usług. Przykładowa aplikacja może być używana jako szablon lub odwołanie do własnych projektów i możesz bezpłatnie kopiować i ponownie używać kodu z książki lub jej przykładów.

Możesz przesłać dalej ten przewodnik do zespołu, aby pomóc w zapewnieniu powszechnej wiedzy na temat tych zagadnień i możliwości. Korzystanie ze wspólnego zestawu terminologii i podstawowych zasad pomaga zapewnić spójne stosowanie wzorców i praktyk architektury.

## <a name="references"></a>Odwołania

- **Witryna sieci Web gRPC**  
  <https://grpc.io>
- **Wybieranie między programami .NET Core i .NET Framework na potrzeby aplikacji serwerowych**  
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[Next](introduction.md)
