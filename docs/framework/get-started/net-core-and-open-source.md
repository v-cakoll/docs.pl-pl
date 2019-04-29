---
title: Oprogramowanie .NET Core i Open-Source
ms.date: 03/30/2017
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5eeef28f9a1d81ffa6328bfa5f2a8ed5295b47aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61644151"
---
# <a name="net-core-and-open-source"></a>Oprogramowanie .NET Core i Open-Source
Ten temat zawiera krótkie omówienie platformy .NET Core, a czego pokazuje, jak można znaleźć więcej informacji. Aby uzyskać pełną listę tematów dla platformy .NET Core, odwiedź stronę [przewodnik platformy .NET Core](../../core/index.md).
  
<a name="BKMK_WhatisNETCore"></a>   
## <a name="what-is-net-core"></a>Co to jest .NET Core?  
 Platforma .NET core to ogólnego przeznaczenia, moduły, dla wielu platform typu open source implementacji .NET Standard. Zawiera on wiele z tych samych interfejsów API jako .NET Framework (ale platformy .NET Core jest mniejszy zestaw) i obejmuje składniki środowiska uruchomieniowego, framework, kompilatora i narzędzi, które obsługują różne systemy operacyjne i mikroukładu elementów docelowych. Wdrożenie platformy .NET Core została zależne głównie przez obciążeń platformy ASP.NET Core, ale również przez konieczność i pragną nowocześniejszego implementacją. Może służyć w urządzeń, chmury i scenariuszach osadzonych IoT.  
  
 Aby rozpocząć pracę z platformą .NET Core, odwiedź stronę [strony głównej platformy .NET Core](https://www.microsoft.com/net/core).  
  
 Poniżej przedstawiono główne cechy platformy .NET Core:  
  
- **Dla wielu platform:** platformy .NET Core udostępnia kluczowe funkcje do wdrożenia funkcji aplikacji zgodnie z potrzebami i ponowne użycie tego kodu, niezależnie od docelowej platformy. Obecnie obsługuje ona trzech głównych systemach operacyjnych (OS): Windows, Linux i macOS. Można napisać aplikacji i bibliotek, które uruchomienie niemodyfikowanego w obsługiwanych systemach operacyjnych. Aby wyświetlić listę obsługiwanych systemów operacyjnych, odwiedź stronę [harmonogram działania dla platformy .NET Core](https://github.com/dotnet/core/blob/master/roadmap.md).
  
- **"Open source":** platformy .NET Core jest jednym z wielu projektów w ramach kształtowanie [.NET Foundation](https://www.dotnetfoundation.org/) i jest dostępna w [GitHub](https://github.com/).  .NET Core jako projekt typu open source o promuje bardziej przejrzyste procesu opracowywania i wspiera aktywne, zaangażowanej społeczności.  
  
- **Elastyczne wdrażanie:** istnieją dwa główne sposoby wdrażania aplikacji: wdrożenie zależny od struktury lub niezależna wdrożenia. Z wdrożeniem zależny od struktury są instalowane tylko zależności aplikacji i innych firm i aplikacji zależy od całego systemu wersję platformy .NET Core, znajdować się.  Z wdrożeniem niezależna wersja platformy .NET Core, używany do tworzenia aplikacji również jest wdrożony wraz z zależności aplikacji i innych firm i uruchomić side-by-side z innymi wersjami.    Aby uzyskać więcej informacji, zobacz [wdrożenie aplikacji programu .NET Core](../../core/deploying/index.md).

- **Modułowy:** platforma .NET Core to moduły, ponieważ jest on zwalniany za pośrednictwem pakietu NuGet w mniejszych pakietów zestawu. Zamiast jeden duży zestaw, który zawiera większość podstawowych funkcji .NET Core jest udostępniany jako mniejszych pakietów skoncentrowane na funkcji. Pozwala bardziej elastyczny model programowania nam oraz pozwala zoptymalizować aplikację, uwzględniając tylko tych pakietów NuGet, których potrzebujesz. Korzyści wynikające z mniejszego obszaru powierzchni aplikacji obejmują większego bezpieczeństwa ograniczona obsługa, zwiększona wydajność i zmniejszyć koszty w modelu płatności dla what-rzeczywiste użycie.  
  
## <a name="the-net-core-platform"></a>Platforma .NET Core  
 Platformy .NET Core składa się z kilku składników, w tym zarządzane kompilatory, środowisko uruchomieniowe, biblioteki klas bazowych i wiele modeli aplikacji, takich jak ASP.NET Core. Dodatkowe informacje na temat różnych składników i Uzyskaj zaangażowane w następującej [GitHub](https://github.com/) repozytoriów:  
  
- [.NET Core](https://github.com/dotnet/core)  
  
- [CoreFX - podstawowe biblioteki .NET Core](https://github.com/dotnet/corefx)  
  
- [CoreCLR — środowisko uruchomieniowe programu .NET Core](https://github.com/dotnet/coreclr)  
  
- [Interfejs wiersza polecenia — narzędzia wiersza polecenia platformy .NET Core](https://github.com/dotnet/cli)  
  
- [Roslyn — platforma kompilatora .NET](https://github.com/dotnet/roslyn)  
  
- [ASP.NET Core](https://github.com/aspnet/home)  
  
## <a name="see-also"></a>Zobacz także

- [Strona główna platformy .NET core](https://www.microsoft.com/net/core)
- [Przewodnik platformy .NET Core](../../core/index.md)
- [Dokumentacja programu ASP.NET Core](/aspnet/core/)
