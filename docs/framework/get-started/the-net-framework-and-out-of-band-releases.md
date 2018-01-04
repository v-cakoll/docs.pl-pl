---
title: Program .NET Framework i wydania poza harmonogramem (OOB)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
caps.latest.revision: "19"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c79326634a24ddcc9aed71fca018c69c36c94db0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="the-net-framework-and-out-of-band-releases"></a>Program .NET Framework i wydania poza harmonogramem (OOB)
Program .NET Framework jest rozwijany, tak aby działał na nowych platformach, takich jak aplikacje Windows Phone i aplikacje do Sklepu Windows, a ponadto obsługiwał tradycyjne aplikacje komputerowe i aplikacje sieci web oraz maksymalizował możliwości ponownego wykorzystania kodu. Oprócz regularnych wersji programu .NET Framework nowe funkcje są udostępniane poza harmonogramem (Out of Band, OOB), aby poprawić programowanie wieloplatformowe lub wprowadzić nowe funkcje. W tym temacie omówiono kierunek rozwoju programu .NET Framework i jego wersji OOB.  
  
## <a name="advantages-of-oob-releases"></a>Zalety wersji OOB  
 Dostarczanie nowych składników lub aktualizacji składników poza harmonogramem umożliwia firmie Microsoft częstsze dostarczanie aktualizacji programu .NET Framework. Umożliwia to także szybsze zbieranie opinii klientów i reagowanie na nie.  
  
 Gdy w aplikacji jest używana funkcja OOB, użytkownicy nie muszą instalować najnowszej wersji programu systemu .NET Framework, aby uruchomić aplikację, ponieważ zestawy OOB są wdrażane z pakietem aplikacji.  
  
## <a name="how-oob-packages-are-distributed"></a>Dystrybucja pakietów OOB  
Wersje OOB dla składników podstawowych wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) są dostarczane za pośrednictwem [NuGet](https://www.nuget.org/), która jest Menedżer pakietów dla platformy .NET. Program NuGet umożliwia łatwe przeglądanie i dodawanie bibliotek do projektów programu .NET Framework z poziomu Eksploratora rozwiązań w programie Visual Studio. Program NuGet jest dołączany do wszystkich wersji programu Visual Studio, począwszy od programu Visual Studio 2012. Aby sprawdzić, czy NuGet jest zainstalowana, należy wyszukać **Menedżer pakietów biblioteki** w programie Visual Studio **narzędzia** menu. Jeśli nie jest zainstalowany:  
  
1.  Na pasku menu programu Visual Studio wybierz **narzędzia**, **rozszerzenia i aktualizacje** (w programie Visual Studio 2010, należy wybrać **Menedżera rozszerzenia**).  
  
     **Rozszerzenia i aktualizacje** zostanie otwarte okno dialogowe.  
  
2.  Wybierz **Online**, **Menedżera pakietów NuGet**, a następnie wybierz pozycję **Pobierz**.  
  
3.  Po zakończeniu pobierania ponownie uruchom program Visual Studio.  
  
 Aby uzyskać szczegółowe instrukcje dotyczące instalacji, zobacz [instalowania NuGet](http://docs.nuget.org/docs/start-here/installing-nuget) w witrynie NuGet dokumentów. Aby uzyskać więcej informacji na temat narzędzia NuGet, zobacz [dokumentacji NuGet](http://docs.nuget.org/).  
  
## <a name="using-a-nuget-oob-package"></a>Używanie pakietu NuGet OOB  
 Po zainstalowaniu programu NuGet można wyszukiwać i dodawać odwołania do pakietów programu NuGet, używając Eksploratora rozwiązań w programie Visual Studio:  
  
1.  Otwórz menu skrótów projektu w programie Visual Studio, a następnie wybierz pozycję **Zarządzaj pakietami NuGet**. (Ta opcja jest dostępna również w **projektu** menu.)  
  
2.  W okienku po lewej stronie wybierz **Online**.  
  
3.  Jeśli chcesz użyć pakiety wersji wstępnej, w polu listy rozwijanej w środkowym okienku, wybierz **obejmują wstępnej** zamiast **tylko stabilne**.  
  
4.  W okienku po prawej stronie, użyj **wyszukiwania** pole, aby zlokalizować pakietu, który chcesz użyć. Niektóre pakiety firmy Microsoft są oznaczone za pomocą logo programu Microsoft .NET Framework, a wszystkie określają firmę Microsoft jako wydawcę.  
  
 ![Menedżer pakietów NuGet](../../../docs/framework/get-started/media/clrnugetdialog.png "clrNugetDialog")  
  
 Jak wspomniano wcześniej, podczas wdrażania aplikacji używającej pakietu OOB zestawy OOB będą dostarczane wraz z pakietem aplikacji.  
  
## <a name="types-of-oob-releases"></a>Typy wersji OOB  
 Zazwyczaj pakiet OOB ma jedną lub kilka wersji wstępnych i wersję stabilną. Licencji, który towarzyszy wstępnej wersji zwykle nie zezwala na redystrybucji, ale pozwala na wypróbowanie pakietu i wyrazić swoją opinię. Opinie są włączane do wszelkich aktualizacji wprowadzanych w pakiecie. Ostateczna wersja jest rozpowszechniana jako stabilny pakiet NuGet i zawiera licencję zezwalającą na dystrybucję pakietu NuGet wraz z aplikacją. Pakiety w wersji stabilnej są obsługiwane przez firmę Microsoft. Firma Microsoft zapewnia obsługę funkcji IntelliSense, a także innych rodzajów dokumentacji, takich jak wpisy na blogu i forum odpowiedzi dla wszystkich pakietów. Ponadto kod źródłowy, mogą być dostępne z niektórych, ale nie wszystkie pakiety. W przypadku anonsów zawierających dotyczących nowych i zaktualizowanych pakietów, można subskrybować [w blogu .NET Framework](http://blogs.msdn.com/b/dotnet/).  
  
 Aby znaleźć pakietów zarówno wersji wstępnej, jak i stabilny, wybierz **obejmują wstępnej** Menedżera pakietów NuGet.  
  
 Jeśli chcesz otrzymywać powiadomienia o wersjach stabilna pakietu subskrybować [źródła danych w programie .NET Framework](https://nuget.org/api/v2/curated-feeds/dotnetframework/Packages/).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../../docs/framework/get-started/index.md)
