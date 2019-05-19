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
ms.openlocfilehash: 4a236b3b4b5c4cde66bad2b460637bb533b764be
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881596"
---
# <a name="reducing-system-restarts-during-net-framework-45-installations"></a>Zmniejszenie liczby ponownych uruchomień systemu podczas instalowania programu .NET Framework 4.5
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalator używa [Menedżera ponownego uruchamiania](https://go.microsoft.com/fwlink/?LinkId=231425) do uniemożliwić systemu powoduje ponowne uruchomienie zawsze, gdy jest to możliwe podczas instalacji. Jeśli program instalacyjny aplikacji instaluje program .NET Framework, mogą łączyć się za pomocą Menedżera ponownego uruchamiania, aby móc korzystać z tej funkcji. Aby uzyskać więcej informacji, zobacz [jak: Pobieranie danych o postępie z Instalatora .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md).  
  
## <a name="reasons-for-a-restart"></a>Ze względu na ponowne uruchomienie  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalacja wymaga ponownego uruchomienia systemu, jeśli aplikacja .NET Framework 4 jest używana podczas instalacji. Jest to spowodowane [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] zastępuje pliki .NET Framework 4 i wymaga tych plików, które będą dostępne podczas instalacji. W wielu przypadkach można zapobiec ponownego uruchomienia przez prewencyjnego wykrywanie i closing.NET Framework 4 aplikacje, które są używane. Jednak niektóre aplikacje systemu nie muszą być zamknięte. W takich przypadkach nie można uniknąć ponownego uruchomienia komputera.  
  
## <a name="end-user-experience"></a>Środowisko użytkownika końcowego  
 Użytkownik końcowy, kto wykonuje pełną instalację programu [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] jest możliwość uniknąć ponownego uruchomienia systemu, jeśli Instalator wykryje aplikacji .NET Framework 4 w użyciu. Komunikat wyświetla listę wszystkich uruchomionych aplikacji .NET Framework 4 i zapewnia możliwość Zamknij te aplikacje, przed rozpoczęciem instalacji. Jeśli użytkownik potwierdzi, te aplikacje są zamykane przez Instalatora, a następnie ponowne uruchomienie systemu jest unikane. Jeśli użytkownik nie odpowiada na komunikat w określonym czasie, instalacja będzie kontynuowana bez zamykania aplikacji.  
  
 Jeśli Menedżera ponownego uruchamiania wykryje sytuację, która będzie wymagać ponownego uruchomienia systemu, nawet wtedy, gdy działające aplikacje zostaną zamknięte, nie jest wyświetlany komunikat.  
  
 ![Okno dialogowe aplikacji Zamknij listę aktualnie uruchomione programy.](./media/reducing-system-restarts/close-application-dialog.png)  
  
## <a name="using-a-chained-installer"></a>Za pomocą Instalatora łańcuchowa  
 Jeśli chcesz wykonać ponowną dystrybucję programu .NET Framework z aplikacją, ale chcesz użyć własnego interfejsu użytkownika i program instalacyjny, proces instalacji (łańcuch) .NET Framework można dołączyć do procesu instalacji. Aby uzyskać więcej informacji na temat instalacji łańcuchowych zobacz [przewodnik wdrażania dla deweloperów](../../../docs/framework/deployment/deployment-guide-for-developers.md). Aby ograniczyć ponowne uruchomienie systemu połączonych urządzeń, Instalatora programu .NET Framework dostarcza listę aplikacji, aby zamknąć program instalacyjny. Program instalacyjny, należy podać te informacje do użytkownika za pomocą interfejsu użytkownika, takich jak okno komunikatu, Uzyskaj odpowiedzi użytkownika, a następnie przekazać odpowiedź z powrotem do Instalatora programu .NET Framework. Na przykład łańcuchowych Instalatora artykuł [jak: Pobieranie danych o postępie z Instalatora .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md).  
  
 Jeśli używasz Instalatora łańcuchowych, ale nie chcesz podać własne okno komunikatu do zamykania aplikacji, można użyć `/showrmui` i `/passive` opcji w wierszu polecenia podczas tworzenia łańcucha programu .NET Framework procesu instalacji. Korzystając z tych opcji razem, Instalator Pokazuje okno komunikatu do zamykania aplikacji, jeśli może zostać zamknięty w celu uniknięcia ponownego uruchomienia systemu. To okno komunikatu działa tak samo w trybie pasywnym, nie pełny interfejs użytkownika. Zobacz [przewodnik wdrażania dla deweloperów](../../../docs/framework/deployment/deployment-guide-for-developers.md) uzyskania pełnego zestawu opcji wiersza polecenia dla pakiet redystrybucyjny programu .NET Framework.  
  
## <a name="see-also"></a>Zobacz także

- [Wdrażanie](../../../docs/framework/deployment/index.md)
- [Przewodnik wdrażania dla deweloperów](../../../docs/framework/deployment/deployment-guide-for-developers.md)
- [Instrukcje: Pobieranie danych o postępie z Instalatora .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)
