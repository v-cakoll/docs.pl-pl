---
title: Tworzenie architektury nowoczesnych aplikacji internetowych za pomocą platformy ASP.NET Core i platformy Azure
description: Przewodnik, który zawiera kompleksowe wskazówki dotyczące tworzenia monolitycznych aplikacji sieci web przy użyciu ASP.NET Core i Azure.
author: ardalis
ms.author: wiwagn
ms.date: 12/4/2019
ms.openlocfilehash: 18449ea02b7f9e89744a0f3088f80b7a51a807da
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987897"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a>Tworzenie architektury nowoczesnych aplikacji internetowych za pomocą platformy ASP.NET Core i platformy Azure

![Zarezerwuj obraz okładki przewodnika Architect Modern Web Applications.](./media/index/web-application-guide-cover-image.png)

**EDITION v3.1** - Zaktualizowano do ASP.NET Core 3.1

OPUBLIKOWANA PRZEZ

Zespoły produktów Microsoft Developer Division, .NET i Visual Studio

Oddział firmy Microsoft Corporation

One Microsoft Way

Redmond, Waszyngton 98052-6399

Prawa autorskie © 2020 roku przez Microsoft Corporation

Wszelkie prawa zastrzeżone. Żadna część zawartości tej książki nie może być powielana ani przekazywana w jakiejkolwiek formie lub w jakikolwiek sposób bez pisemnej zgody wydawcy.

Książka ta jest dostarczana "tak jak jest" i wyraża poglądy i opinie autora. Poglądy, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odniesienia do stron internetowych, mogą ulec zmianie bez powiadomienia.

Niektóre z przykładów przedstawiono wyłącznie do celów informacyjnych i są one fikcyjne. Żadne rzeczywiste skojarzenia lub związki nie są zamierzone ani wnioskowane.

Firma Microsoft i znaki https://www.microsoft.com towarowe wymienione na stronie internetowej "Znaki towarowe" są znakami towarowymi grupy firm Microsoft.

Mac i macOS są znakami towarowymi firmy Apple Inc.

Logo docker wielorybów jest zastrzeżonym znakiem towarowym firmy Docker, Inc. Używany za zgodą.

Wszystkie inne znaki i logo są własnością ich odpowiednich właścicieli.

Autor:

> **Steve "ardalis" Smith** - Architekt oprogramowania i trener - [Ardalis.com](https://ardalis.com)

Edytory:

> **Maira Wenzel**

## <a name="introduction"></a>Wprowadzenie

.NET Core i ASP.NET Core oferują kilka zalet w stosunku do tradycyjnego rozwoju platformy .NET. Należy użyć .NET Core dla aplikacji serwera, jeśli niektóre lub wszystkie z następujących są ważne dla sukcesu aplikacji:

- Obsługa międzyplatformowa.

- Korzystanie z mikrousług.

- Korzystanie z kontenerów platformy Docker.

- Wymagania dotyczące wysokiej wydajności i skalowalności.

- Przechowywanie wersji obok siebie wersji platformy .NET przez aplikację na tym samym serwerze.

Tradycyjne aplikacje platformy .NET mogą i obsługują wiele z tych wymagań, ale ASP.NET Core i .NET Core zostały zoptymalizowane w celu zaoferowania ulepszonej obsługi powyższych scenariuszy.

Coraz więcej organizacji decyduje się na hostowania swoich aplikacji sieci web w chmurze przy użyciu usług, takich jak Microsoft Azure. Należy rozważyć hostowanie aplikacji w chmurze, jeśli są ważne dla aplikacji lub organizacji:

- Mniejsze inwestycje w koszty centrów danych (sprzęt, oprogramowanie, przestrzeń, narzędzia, zarządzanie serwerami itp.)

- Elastyczne ceny (wynagrodzenie oparte na użyciu, a nie na bezczynności).

- Ekstremalna niezawodność.

- Ulepszona mobilność aplikacji; łatwo zmienić miejsce i sposób wdrażania aplikacji.

- Elastyczna pojemność; w górę lub w dół w zależności od rzeczywistych potrzeb.

Tworzenie aplikacji sieci web za pomocą ASP.NET Core, hostowanych na platformie Azure, oferuje wiele korzyści konkurencyjnych w stosunku do tradycyjnych alternatyw. ASP.NET Core jest zoptymalizowany pod kątem nowoczesnych praktyk tworzenia aplikacji sieci web i scenariuszy hostingu w chmurze. W tym przewodniku dowiesz się, jak zaprojektować aplikacje ASP.NET Core, aby jak najlepiej wykorzystać te możliwości.

## <a name="purpose"></a>Przeznaczenie

Ten przewodnik zawiera kompleksowe wskazówki dotyczące tworzenia *monolitycznych* aplikacji sieci web przy użyciu ASP.NET Core i azure. W tym kontekście "monolityczne" odnosi się do faktu, że te aplikacje są wdrażane jako pojedyncza jednostka, a nie jako zbiór interakcji usług i aplikacji.

Ten przewodnik jest uzupełnieniem ["_.NET Microservices. Architektura konteneryzowanych aplikacji .NET_",](../microservices/index.md) która koncentruje się bardziej na platformie Docker, Mikrousług i wdrażaniu kontenerów do obsługi aplikacji korporacyjnych.

### <a name="net-microservices-architecture-for-containerized-net-applications"></a>Mikrousług .NET. architektura konteneryzowanych aplikacji .NET

- **książka elektroniczna**  
  <https://aka.ms/MicroservicesEbook>
- **Przykładowa aplikacja**  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a>Kto powinien korzystać z tego przewodnika

Odbiorcami tego przewodnika są głównie deweloperzy, potencjalni klienci programiści i architekci, którzy są zainteresowani tworzeniem nowoczesnych aplikacji sieci Web przy użyciu technologii i usług firmy Microsoft w chmurze.

Dodatkową grupą odbiorców są decydenci techniczni, którzy są już znani ASP.NET lub platformy Azure i szukają informacji na temat tego, czy warto uaktualnić do ASP.NET Core dla nowych lub istniejących projektów.

## <a name="how-you-can-use-this-guide"></a>Jak można korzystać z tego przewodnika

Ten przewodnik został skondensowany w stosunkowo mały dokument, który koncentruje się na tworzeniu aplikacji sieci web z nowoczesnymi technologiami platformy .NET i systemem Windows Azure. Jako takie, można go odczytać w całości, aby zapewnić podstawę zrozumienia takich zastosowań i ich względów technicznych. Przewodnik, wraz z jego przykładową aplikacją, może również służyć jako punkt wyjścia lub odniesienia. Użyj skojarzonej przykładowej aplikacji jako szablonu dla własnych aplikacji lub aby zobaczyć, jak można zorganizować części składowe aplikacji. Zapoznaj się z zasadami przewodnika oraz zakresem opcji architektury i technologii oraz zagadnieniami decyzyjnymi podczas ważenia tych opcji dla własnego zastosowania.

Możesz przesłać ten przewodnik do swojego zespołu, aby zapewnić wspólne zrozumienie tych zagadnień i możliwości. Posiadanie wszystkich pracujących z wspólnego zestawu terminologii i podstawowych zasad pomaga zapewnić spójne stosowanie wzorców i praktyk architektonicznych.

## <a name="references"></a>Dokumentacja

- **Wybieranie między programami .NET Core i .NET Framework na potrzeby aplikacji serwerowych**  
  [https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server](../../standard/choosing-core-framework-server.md)

>[!div class="step-by-step"]
>[Dalej](modern-web-applications-characteristics.md)
