---
title: "Architektów nowoczesnych aplikacji sieci web platformy ASP.NET Core i Azure"
description: Projektowania nowoczesnych aplikacji sieci Web platformy ASP.NET Core i Azure | wprowadzenie
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 44864274a86634c0199885b5507124f2f54ce0f6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a>Architektów nowoczesnych aplikacji sieci Web platformy ASP.NET Core i Azure

Oprogramowanie .NET core i ASP.NET Core oferują wiele zalet w porównaniu do tradycyjnego .NET — rozwój. Jeśli niektóre lub wszystkie z następujących czynności są ważne, aby wskazywał Powodzenie, aplikacji, należy użyć .NET Core dla aplikacji serwera:

-   Obsługa platform

-   Użyj mikrousług

-   Używanie kontenerów Docker

-   Wymagania dotyczące wysokiej wydajności i skalowalności

-   Przechowywanie wersji Side-by-side wersji platformy .NET przez aplikację na tym samym serwerze

Tradycyjne aplikacje .NET mogą i obsługują tych wymagań, ale .NET Core i ASP.NET Core zostały zoptymalizowane do oferują ulepszoną obsługę powyższych scenariuszy.

Organizacje coraz więcej wybierania do obsługi aplikacji sieci web w chmurze przy użyciu usługi Microsoft Azure. Należy rozważyć obsługę aplikacji w chmurze, czy następujące usługi są ważne do aplikacji lub organizacji:

-   Inwestycji zmniejszenie kosztów centrum danych (sprzętu, oprogramowania, miejsca, narzędzia itp.)

-   Elastyczne cennik (płatności na podstawie użycia nie dla bezczynności pojemności)

-   Extreme niezawodności

-   Mobilność aplikacji została poprawiona; łatwo zmienić, jak i gdzie wdrożonej aplikacji

-   Elastyczna pojemność; Skalowanie w górę lub w dół na podstawie rzeczywistych potrzeb

Tworzenie aplikacji sieci web platformy ASP.NET Core, obsługiwane na platformie Microsoft Azure oferuje wiele przewagi konkurencyjnej nad alternatyw tradycyjnych. Platformy ASP.NET Core jest zoptymalizowana pod kątem rozwiązania w zakresie tworzenia nowoczesnych witryn sieci web aplikacji i scenariusze hostingu w chmurze. W tym przewodniku dowiesz się, jak zaprojektować najlepiej wykorzystać te możliwości aplikacji platformy ASP.NET Core.

## <a name="purpose"></a>Cel

W tym przewodniku znajdują się na trasie wskazówki dotyczące tworzenia aplikacji sieci web wbudowanymi za pomocą platformy ASP.NET Core i Azure.

Ten przewodnik jest uzupełniające "*Architecting i tworzenie konteneryzowanych i aplikacji z platformą .NET Mikrousługi*" do hosta przedsiębiorstwa który skupia się więcej na Docker Mikrousług oraz wdrożenia kontenerów aplikacje.

> ### <a name="architecting-and-developing-containerized-microservice-based-apps-in-net"></a>Projektowania i opracowywania konteneryzowanych Mikrousługi na podstawie aplikacji w .NET
> - **Książka elektroniczna**  
> <http://aka.MS/MicroservicesEbook>
> - **Przykładowa aplikacja**  
> <http://aka.MS/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a>Kto powinien używać ten przewodnik

Odbiorcami tego przewodnika jest głównie deweloperom, programowanie potencjalnych klientów i architektów zainteresowanych tworzenie nowoczesnych aplikacji sieci web przy użyciu usług i technologii firmy Microsoft w chmurze.

Dodatkowej odbiorców jest techniczne inne osoby podejmujące decyzje, które są już znane ASP.NET i/lub Azure i szukasz informacji na temat tego, czy dobrym rozwiązaniem jest uaktualnienie do platformy ASP.NET Core dla nowych lub istniejących projektów.

## <a name="how-you-can-use-this-guide"></a>Sposób korzystania z tego przewodnika

Ten przewodnik zawiera zostały zmniejszenia dokumentem stosunkowo mały, który koncentruje się na tworzeniu aplikacji sieci web z nowoczesnej technologii .NET i systemu Windows Azure. W efekcie mogą być odczytywane w całości, aby zapewnić podstawę zrozumienia takich aplikacji i ich zagadnienia techniczne. Przewodnik, wraz z przykładowej aplikacji, mogą również służyć jako punktu wyjścia lub odwołanie. Użyj skojarzone przykładowej aplikacji jako szablonu dla własnej aplikacji lub sprawdzić, jak mogą organizować części aplikacji. Odwołują się do zasad i pokrycia architektury i opcje technologii i zagadnienia dotyczące decyzji Przewodnik po o wadze tych opcji dla swojej aplikacji.

Możesz przesłać ten przewodnik do zespołu w celu zapewnienia zrozumienie tych zagadnień i możliwości. Każdy Praca ze wspólnego zestawu terminologii i podstawowymi zasadami o pomoże zapewnienia spójnego stosowania wzorców architektury rozwiązania.

## <a name="references"></a>Odwołania
- **Wybieranie między programami .NET Core i .NET Framework na potrzeby aplikacji serwerowych**  
<https://docs.microsoft.com/DotNet/articles/Standard/Choosing-Core-Framework-Server>

>[!div class="step-by-step"]
[Next] (modern-web aplikacje characteristics.md)
