---
title: Oprogramowanie .NET Core i Open-Source
ms.date: 03/30/2017
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 707e73705e5e96e1b0b92976d22f763afef64929
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389255"
---
# <a name="net-core-and-open-source"></a>Oprogramowanie .NET Core i Open-Source
Ten temat zawiera krótki przegląd co .NET Core i pokazuje, jak można znaleźć więcej informacji. Aby uzyskać pełną listę tematów dla platformy .NET Core, odwiedź stronę [.NET Core przewodnik](../../core/index.md).
  
<a name="BKMK_WhatisNETCore"></a>   
## <a name="what-is-net-core"></a>Co to jest oprogramowanie .NET Core?  
 Oprogramowanie .NET core jest ogólnego przeznaczenia, implementacja moduły, obsługujący wiele platform i otwórz źródła .NET Standard. Zawiera on wiele z tych samych interfejsów API jako programu .NET Framework (ale .NET Core jest mniejszy zestaw) i obejmuje składniki środowiska uruchomieniowego, framework, narzędzi i kompilatora, które obsługują różnych systemów operacyjnych i układu obiektów docelowych. Implementacja .NET Core została zależne głównie przez obciążeń platformy ASP.NET Core, ale również przez muszą i chcesz bardziej nowoczesnych implementacją. Może służyć w urządzenia, chmur i scenariusze osadzonych IoT.  
  
 Aby rozpocząć pracę z platformą .NET Core, przejdź na stronę [strony głównej platformy .NET Core](https://www.microsoft.com/net/core).  
  
 Poniżej przedstawiono głównych cech usługi .NET Core:  
  
-   **Obsługujący wiele platform:** .NET Core zawiera najważniejsze funkcje do implementowania funkcji aplikacji, należy go i ponownie wykorzystać ten kod, niezależnie od docelowego platformy. Obecnie obsługuje trzy główne systemy operacyjne (systemu operacyjnego): Windows, Linux lub macOS. Można pisać aplikacje i bibliotek, które zostały zmodyfikowane spotkać obsługiwanych systemów operacyjnych. Aby wyświetlić listę obsługiwanych systemów operacyjnych, odwiedź stronę [plan .NET Core](https://github.com/dotnet/core/blob/master/roadmap.md).
  
-   **Typu open source:** .NET Core jest jednym z wielu projektów w obszarze zarządzania programu [.NET Foundation](http://www.dotnetfoundation.org/) i jest dostępny w [GitHub](https://github.com/).  O .NET Core jako projekt typu open source wspiera bardziej przejrzyste procesu projektowania i wspiera active i zaangażowani społeczności.  
  
-   **Elastyczne wdrażanie:** istnieją dwa sposoby wdrażania aplikacji: wdrażania zależne od framework lub niezależne wdrożenia. Z wdrożeniem framework zależne są instalowane tylko zależności aplikacji i innych firm i aplikacji zależy od wersji systemu .NET Core znajdować się.  Z wdrożeniem niezależna wersja platformy .NET Core używany do tworzenia aplikacji również jest wdrażany wraz z zależności aplikacji i innych firm i uruchomić side-by-side z innymi wersjami.    Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji .NET Core](../../core/deploying/index.md).

-   **Moduły:** .NET Core jest moduły, ponieważ jego zwolnienia za pośrednictwem pakietu NuGet w mniejszych pakietów zestawu. Zamiast jeden duży zestaw, który zawiera większość podstawowych funkcji .NET Core staje się dostępna jako mniejszych pakietów skoncentrowane na funkcji. Umożliwia firmie Microsoft był bardziej elastyczny model programowania i umożliwia optymalizowanie aplikacji obejmują tylko pakietów NuGet, które są potrzebne. Mniejsze powierzchni aplikacji zalety większego bezpieczeństwa obniżona Obsługa, poprawioną wydajność i zmniejszyć koszty w modelu płatności do co — użytkownik użycia.  
  
## <a name="the-net-core-platform"></a>Podstawowej platformy .NET  
 Platforma .NET Core składa się z kilku składników, w tym zarządzanych kompilatory, środowiska uruchomieniowego bibliotek klasy podstawowej i wiele modeli aplikacji, takich jak ASP.NET Core. Dodatkowe informacje na temat różnych składników i pobrać zaangażowane w następującej [GitHub](https://github.com/) repozytoriów:  
  
-   [.NET Core](https://github.com/dotnet/core)  
  
-   [CoreFX - podstawowych bibliotek .NET Core](https://github.com/dotnet/corefx)  
  
-   [Środowisko CoreCLR - podstawowego środowiska wykonawczego .NET](https://github.com/dotnet/coreclr)  
  
-   [Interfejs wiersza polecenia — narzędzia wiersza polecenia platformy .NET Core](https://github.com/dotnet/cli)  
  
-   [Roslyn - platformę .NET kompilatora](https://github.com/dotnet/roslyn)  
  
-   [ASP.NET Core](https://github.com/aspnet/home)  
  
## <a name="see-also"></a>Zobacz też  
 [Strona główna platformy .NET core](https://www.microsoft.com/net/core)  
 [Przewodnik platformy .NET Core](../../core/index.md)  
 [Dokumentacja platformy ASP.NET Core](/aspnet/core/)
