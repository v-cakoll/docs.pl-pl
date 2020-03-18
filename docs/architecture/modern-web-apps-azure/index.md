---
title: Architekt nowoczesnych aplikacji internetowych z ASP.NET Core i Azure
description: Przewodnik, który zawiera kompleksowe wskazówki dotyczące tworzenia monolitycznych aplikacji sieci web przy użyciu ASP.NET Core i Azure.
author: ardalis
ms.author: wiwagn
ms.date: 12/4/2019
ms.openlocfilehash: c19e5e90cfb96463f744cfb064abe72ee5db2e9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77449334"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a>Tworzenie architektury nowoczesnych aplikacji internetowych za pomocą platformy ASP.NET Core i platformy Azure

![Zarezerwuj okładkę przewodnika Architect Modern Web Applications.](./media/index/web-application-guide-cover-image.png)

**EDITION v3.1** - Zaktualizowano do ASP.NET Core 3.1

OPUBLIKOWANA PRZEZ

Zespoły produktów Microsoft Developer Division, .NET i Visual Studio

Oddział Firmy Microsoft Corporation

One Microsoft Way

Redmond (Waszyngton) 98052-6399

Prawa autorskie © 2020 r. przez Firmę Microsoft Corporation

Wszelkie prawa zastrzeżone. Żadna część treści tej książki nie może być powielana lub przekazywana w jakiejkolwiek formie lub w jakikolwiek sposób bez pisemnej zgody wydawcy.

Ta książka jest "tak jak jest" i wyraża poglądy i opinie autora. Poglądy, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odniesienia do stron internetowych, mogą ulec zmianie bez powiadomienia.

Niektóre z przykładów przedstawiono wyłącznie do celów informacyjnych i są one fikcyjne. Żadne rzeczywiste skojarzenia lub związki nie są zamierzone ani wnioskowane.

Microsoft i znaki towarowe https://www.microsoft.com wymienione na stronie internetowej "Znaki towarowe" są znakami towarowymi grupy firm Microsoft.

Mac i macOS są znakami towarowymi firmy Apple Inc.

Logo wieloryba Docker jest zastrzeżonym znakiem towarowym firmy Docker, Inc. Używanym za zgodą.

Wszystkie inne znaki i logo są własnością ich właścicieli.

Autor:

> **Steve "ardalis" Smith** - Architekt oprogramowania i trener - [Ardalis.com](https://ardalis.com)

Edytory:

> **Maira Wenzel**

## <a name="introduction"></a>Wprowadzenie

.NET Core i ASP.NET Core oferują kilka zalet w porównaniu z tradycyjnym rozwojem .NET. Należy użyć .NET Core dla aplikacji serwera, jeśli niektóre lub wszystkie z następujących są ważne dla powodzenia aplikacji:

- Obsługa międzyplatformowa.

- Korzystanie z mikrousług.

- Korzystanie z kontenerów platformy Docker.

- Wysoka wydajność i skalowalność wymagania.

- Side-by-side przechowywanie wersji programu .NET przez aplikację na tym samym serwerze.

Tradycyjne aplikacje .NET mogą i obsługują wiele z tych wymagań, ale ASP.NET Core i .NET Core zostały zoptymalizowane w celu zaoferowania ulepszonej obsługi powyższych scenariuszy.

Coraz więcej organizacji decyduje się na hostowanie swoich aplikacji sieci web w chmurze przy użyciu usług, takich jak Microsoft Azure. Należy rozważyć hosting aplikacji w chmurze, jeśli następujące są ważne dla aplikacji lub organizacji:

- Mniejsze inwestycje w koszty centrów danych (sprzęt, oprogramowanie, przestrzeń, narzędzia, zarządzanie serwerami itp.)

- Elastyczne ceny (płatność na podstawie użycia, a nie bezczynności).

- Ekstremalna niezawodność.

- Ulepszona mobilność aplikacji; łatwo zmienić miejsce i sposób wdrażania aplikacji.

- Elastyczna pojemność; w górę lub w dół w zależności od rzeczywistych potrzeb.

Tworzenie aplikacji sieci Web z ASP.NET Core, hostowanym na platformie Azure, oferuje wiele przewag konkurencyjnych w porównaniu z tradycyjnymi alternatywami. ASP.NET Core jest zoptymalizowany pod kątem nowoczesnych praktyk tworzenia aplikacji sieci web i scenariuszy hostingu w chmurze. W tym przewodniku dowiesz się, jak zaprojektować swoje ASP.NET aplikacje podstawowe, aby jak najlepiej wykorzystać te możliwości.

## <a name="purpose"></a>Przeznaczenie

Ten przewodnik zawiera kompleksowe wskazówki dotyczące tworzenia *monolitycznych* aplikacji sieci web przy użyciu ASP.NET Core i Azure. W tym kontekście "monolityczne" odnosi się do faktu, że te aplikacje są wdrażane jako pojedyncza jednostka, a nie jako zbiór usług interakcji i aplikacji.

Ten przewodnik jest uzupełnieniem ["_Mikrousług .NET. Architektura konteneryzowanych aplikacji .NET_",](../microservices/index.md) która koncentruje się bardziej na platformie Docker, Mikrousługach i wdrażaniu kontenerów do hostowania aplikacji dla przedsiębiorstw.

### <a name="net-microservices-architecture-for-containerized-net-applications"></a>Mikrousług .NET. architektura konteneryzowanych aplikacji .NET

- **książka elektroniczna**  
  <https://aka.ms/MicroservicesEbook>
- **Przykładowa aplikacja**  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a>Kto powinien skorzystać z tego przewodnika

Odbiorcami tego przewodnika są głównie deweloperzy, potencjalni klienci i architekci zainteresowani tworzeniem nowoczesnych aplikacji internetowych przy użyciu technologii i usług firmy Microsoft w chmurze.

Dodatkowa grupa odbiorców to decydenci techniczni, którzy są już zaznajomieni ASP.NET lub platformie Azure i szukają informacji na temat tego, czy warto uaktualnić do ASP.NET Core dla nowych lub istniejących projektów.

## <a name="how-you-can-use-this-guide"></a>Jak korzystać z tego przewodnika

Ten przewodnik został skondensowany do stosunkowo małego dokumentu, który koncentruje się na tworzeniu aplikacji sieci web przy zastosowaniu nowoczesnych technologii .NET i systemu Windows Azure. W związku z tym można je przeczytać w całości, aby zapewnić podstawę zrozumienia takich zastosowań i ich względów technicznych. Przewodnik, wraz z jego przykładowej aplikacji, może również służyć jako punkt wyjścia lub odniesienia. Użyj skojarzonej przykładowej aplikacji jako szablonu dla własnych aplikacji lub aby zobaczyć, jak można zorganizować części składowe aplikacji. Zapoznaj się z zasadami przewodnika i zakresarchitektury i technologii opcji i zagadnień decyzji, gdy jesteś ważenia tych wyborów dla własnej aplikacji.

Nie krępuj się przekazać ten przewodnik do swojego zespołu, aby zapewnić wspólne zrozumienie tych rozważań i możliwości. Posiadanie wszystkich pracujących na podstawie wspólnego zestawu terminologii i podstawowych zasad pomaga zapewnić spójne stosowanie wzorców i praktyk architektonicznych.

## <a name="references"></a>Dokumentacja

- **Wybieranie między programami .NET Core i .NET Framework na potrzeby aplikacji serwerowych**  
  [https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server](../../standard/choosing-core-framework-server.md)

>[!div class="step-by-step"]
>[Dalej](modern-web-applications-characteristics.md)
