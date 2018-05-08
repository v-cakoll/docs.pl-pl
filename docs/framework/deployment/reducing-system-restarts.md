---
title: Zmniejszenie liczby ponownych uruchomień systemu podczas instalowania programu .NET Framework 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework, reducing system restarts
- installing .NET Framework
- installation [.NET Framework]
ms.assetid: 7aa8cb72-dee9-4716-ac54-b17b9ae8218f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e54dcb585c06f2bf49c41f763e03e5624a033442
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="reducing-system-restarts-during-net-framework-45-installations"></a>Zmniejszenie liczby ponownych uruchomień systemu podczas instalowania programu .NET Framework 4.5
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalator używa [ponownie uruchom Menedżera](http://go.microsoft.com/fwlink/?LinkId=231425) zapobiegające system uruchamia ponownie w miarę możliwości podczas instalacji. Jeśli program Instalator aplikacji instaluje program .NET Framework, mogą łączyć się z menedżerem Uruchom ponownie, aby móc korzystać z tej funkcji. Aby uzyskać więcej informacji, zobacz [porady: uzyskiwanie postępie z Instalatora .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md).  
  
## <a name="reasons-for-a-restart"></a>Ze względu na ponowne uruchomienie  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalacja wymaga ponownego uruchomienia systemu, jeśli aplikacji .NET Framework 4 jest używany podczas instalacji. Jest to spowodowane [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] zastępuje pliki programu .NET Framework 4 i wymaga tych plików, które będą dostępne podczas instalacji. W wielu przypadkach można zapobiec ponownego uruchomienia przez preemptively wykrywanie i closing.NET Framework 4 aplikacje, które są używane. Jednak niektóre aplikacje systemu nie powinien zostać zamknięty. W takim przypadku nie można uniknąć ponownego uruchomienia komputera.  
  
## <a name="end-user-experience"></a>Środowisko użytkownika końcowego  
 Użytkownik końcowy, który jest wykonanie pełnej instalacji programu [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ma możliwość Aby uniknąć ponownego uruchomienia systemu, jeśli Instalator wykryje aplikacji .NET Framework 4 w użyciu. Komunikat zawiera listę wszystkich uruchomionych aplikacji .NET Framework 4 i udostępnia opcję Zamknij te aplikacje przed rozpoczęciem instalacji. Jeśli użytkownik potwierdza, te aplikacje są zamknięte przez Instalatora i uniknąć ponownego uruchomienia systemu. Jeśli użytkownik nie odpowiada na komunikat w określonym czasie, instalacja będzie kontynuowana bez zamykania żadnych aplikacji.  
  
 Jeśli ponowne uruchomienie Menedżera wykryje sytuację, której będzie wymagać ponownego uruchomienia systemu, nawet jeśli uruchamianie aplikacji są zamknięte, nie zostanie wyświetlony komunikat.  
  
 ![Zamknij okno dialogowe aplikacji](../../../docs/framework/deployment/media/closeapplicationdialog.png "CloseApplicationDialog")  
Monituj o zamknięcie aplikacji .NET Framework, które są używane  
  
## <a name="using-a-chained-installer"></a>Za pomocą Instalatora łańcuchowa  
 Jeśli chcesz wykonać ponowną dystrybucję .NET Framework za pomocą aplikacji, ale chcesz użyć własnego interfejsu użytkownika i program instalacyjny, proces instalacji (łańcucha) programu .NET Framework można dołączyć do procesu instalacji. Aby uzyskać więcej informacji na temat instalacji łańcuchowa zobacz [przewodnik wdrażania dla deweloperów](../../../docs/framework/deployment/deployment-guide-for-developers.md). Aby ograniczyć liczbę ponownych uruchomień systemu w instalacjach łańcuchowa, Instalator .NET Framework udostępnia programu Instalatora z listą zamknięcie aplikacji. Program Instalator musi podać te informacje użytkownika za pomocą interfejsu użytkownika, takich jak okno komunikatu, pobrać odpowiedzi użytkownika, a następnie przekazać odpowiedź do Instalatora .NET Framework. Na przykład łańcuchowa Instalatora, zobacz artykuł [porady: uzyskiwanie postępie z Instalatora .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md).  
  
 Jeśli używasz łańcuchowa Instalatora, ale nie chcesz podać własne okno komunikatu zamknięcia aplikacji, można użyć `/showrmui` i `/passive` procesie instalacji opcje wiersza polecenia podczas tworzenia łańcucha programu .NET Framework. Jeśli korzystasz ze sobą te opcje, Instalator zawiera komunikat zamknięcia aplikacji, jeśli może zostać zamknięty w celu uniknięcia ponownego uruchomienia systemu. To okno komunikatu działa tak samo w trybie pasywnym, nie pełny interfejs użytkownika. Zobacz [przewodnik wdrażania dla deweloperów](../../../docs/framework/deployment/deployment-guide-for-developers.md) dla pełny zestaw opcji wiersza polecenia dla pakietu redystrybucyjnego programu .NET Framework.  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażanie](../../../docs/framework/deployment/index.md)  
 [Przewodnik wdrażania dla deweloperów](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 [Instrukcje: Pobieranie danych o postępie z Instalatora .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)
