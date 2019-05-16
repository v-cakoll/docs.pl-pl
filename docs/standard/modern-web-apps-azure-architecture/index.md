---
title: Projektowania nowoczesnych aplikacji sieci web za pomocą platformy ASP.NET Core i platformy Azure
description: Przewodnik, który dostarcza wskazówki end-to-end na tworzeniu aplikacji monolitycznych internetowych przy użyciu platformy ASP.NET Core i platformy Azure.
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 0b29a407ae18f3ce0c7499c75ee3c888296102c2
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639306"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a>Projektowania nowoczesnych aplikacji sieci Web za pomocą platformy ASP.NET Core i platformy Azure

![Obejmuje obraz przewodnik architektury nowoczesnych aplikacji sieci Web.](./media/index/web-application-guide-cover-image.png)

OPUBLIKOWANE PRZEZ

Zespoły produktu Microsoft Developer Division, .NET i Visual Studio

Dzielenie firmy Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2019 przez firmę Microsoft Corporation

Wszelkie prawa zastrzeżone. Nie części zawartości tej książki może odtworzyć lub przenoszone w jakiejkolwiek formie lub za pomocą jakichkolwiek środków bez pisemnej zgody wydawcy.

Ten podręcznik jest dostarczany "jako — jest" i wyraża, widoki i opinie od autora. Widoki, opinie i informacje wyrażone w tym podręczniku, w tym adresy URL i inne odnośniki do witryn internetowych, mogą ulec zmianie bez powiadomienia.

Niektóre przedstawione przykłady znajdują się wyłącznie do celów informacyjnych i są fikcyjne. Nie rzeczywiste skojarzenia ani powiązania nie są zamierzone ani powinny być zakładane.

Firma Microsoft i znaków towarowych, opisane w temacie https://www.microsoft.com na stronie sieci Web "Znakami" są znakami towarowymi grupy firm Microsoft.

Komputery Mac i z systemem macOS są znakami towarowymi firmy Apple Inc.

Logo whale platformy Docker jest zastrzeżonym znakiem towarowym firmy Docker, Inc. Używane przez uprawnienia.

Wszystkie inne znaki i logo są własnością ich prawnych właścicieli.

Autor:

> **Steve "ardalis" Smith** — architekt oprogramowania i Trainer — [Ardalis.com](https://ardalis.com)

Edytory:

> **Maira Wenzel**

## <a name="introduction"></a>Wprowadzenie

.NET core i ASP.NET Core oferują wiele zalet w porównaniu do tradycyjnego programowania na platformie .NET. Jeśli niektóre lub wszystkie z następujących czynności są ważne dla Powodzenie swojej aplikacji, należy użyć platformy .NET Core dla aplikacji serwera:

- Obsługa wielu platform.

- Korzystanie z mikrousług.

- Korzystanie z kontenerów platformy Docker.

- Wymagania wysokiej wydajności i skalowalności.

- Side-by-side wersji programu .NET w wersji przez aplikację na tym samym serwerze.

Tradycyjne aplikacje .NET można i należy obsługiwać wiele z tych wymagań, ale platformy ASP.NET Core i .NET Core zostały zoptymalizowane do zaoferowania Ulepszona obsługa dla powyższych scenariuszy.

Coraz więcej organizacji decyduje się na hostowanie aplikacji sieci web w chmurze przy użyciu usług takich jak Microsoft Azure. Należy rozważyć obsługę aplikacji w chmurze, jeśli następujące usługi są ważne do aplikacji lub organizacji:

- Zmniejszenie zwrot z inwestycji w kosztów centrum danych (sprzętu, oprogramowania, miejsca, narzędzia, Zarządzanie serwerem, itp.)

- Elastyczny cennik (płatność na podstawie użycia, nie za bezczynną dyspozycyjność).

- Extreme niezawodność.

- Mobilność aplikacji została poprawiona; łatwo zmienić, gdzie i w jaki sposób Twoja aplikacja jest wdrożona.

- Elastyczna pojemność; Skalowanie w górę lub w dół na podstawie rzeczywistych potrzeb.

Tworzenie aplikacji sieci web za pomocą programu ASP.NET Core, hostowanych na platformie Azure, oferuje wiele przewagi nad alternatyw tradycyjnych. Platforma ASP.NET Core jest zoptymalizowany pod kątem wytwarzania oprogramowania aplikacji nowoczesne rozwiązania sieci web i w chmurze, w scenariuszach hostingu. W tym przewodniku dowiesz się, jak zaprojektować najlepsze wykorzystanie tych możliwości aplikacji platformy ASP.NET Core.

## <a name="purpose"></a>Cel

Ten przewodnik zawiera end-to-end wskazówki dotyczące tworzenia aplikacji *monolityczne* aplikacji internetowych za pomocą platformy ASP.NET Core i platformy Azure. W tym kontekście "monolitycznych" odnosi się do faktu, że te aplikacje są wdrażane jako pojedynczą jednostkę, a nie jako zbiór interakcje usługi i aplikacje.

Ten przewodnik jest uzupełnieniem ["_Mikrousługi .NET. Architektura aplikacji kontenerowych nimi .NET_"](../microservices-architecture/index.md) hostowanie aplikacji przedsiębiorstwa który skupia się więcej na platformy Docker, Mikrousługi i wdrażanie kontenerów.

### <a name="net-microservices-architecture-for-containerized-net-applications"></a>Mikrousługi .NET. architektura konteneryzowanych aplikacji .NET

- **e-book**  
  <https://aka.ms/MicroservicesEbook>
- **Przykładowa aplikacja**  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a>Kto powinien używać tego przewodnika

Odbiorcami tego przewodnika jest przede wszystkim deweloperom, kierownikami ds. programowania i architektów, którzy są zainteresowani tworzenia nowoczesnych aplikacji internetowych przy użyciu technologii firmy Microsoft i usługi w chmurze.

Pomocniczy odbiorców jest techniczne inne osoby podejmujące decyzje, którzy już znanych ASP.NET lub na platformie Azure i szukasz informacji na temat tego, czy warto uaktualnić do programu ASP.NET Core dla nowych lub istniejących projektów.

## <a name="how-you-can-use-this-guide"></a>Jak można użyć tego przewodnika

Ten przewodnik zawiera zostało zmniejszone do stosunkowo mały dokument, który koncentruje się na tworzeniu aplikacji sieci web za pomocą nowoczesnych technologii .NET i usługi Windows Azure. W efekcie mogą być odczytywane w całości, aby zapewnić podstawę zrozumienia tego typu aplikacji i ich zagadnienia techniczne. Przewodnik, wraz z przykładowej aplikacji, może również służyć jako punkt początkowy lub odwołania. Skojarzone przykładowej aplikacji należy użyć jako szablonu dla własnych aplikacjach lub aby zobaczyć, jak możesz organizować części składnika swojej aplikacji. Odnoszą się do zasad i pokrycie architektury i technologii opcje i zagadnienia dotyczące decyzji Przewodnik po należy zwrócić uwagę na te opcje dla swojej aplikacji.

Możesz przekazywać tego przewodnika, aby Twój zespół do pomagają zagwarantować, że te zagadnienia i możliwości. Posiadanie wszystkich działa z wspólny zbiór terminologii i podstawowymi zasadami pomaga zapewnić spójnego stosowania architektury wzorców i praktyk.

## <a name="references"></a>Odwołania

- **Wybieranie między programami .NET Core i .NET Framework na potrzeby aplikacji serwerowych**  
  [https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server](../choosing-core-framework-server.md)

>[!div class="step-by-step"]
>[Next](modern-web-applications-characteristics.md)
