---
title: Zmniejszenie liczby ponownych uruchomień systemu podczas instalowania programu .NET Framework 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework, reducing system restarts
- installing .NET Framework
- installation [.NET Framework]
ms.assetid: 7aa8cb72-dee9-4716-ac54-b17b9ae8218f
ms.openlocfilehash: 6261a883e7b99b7fd38da2a17ab4820c81552506
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75716429"
---
# <a name="reducing-system-restarts-during-net-framework-45-installations"></a>Zmniejszenie liczby ponownych uruchomień systemu podczas instalowania programu .NET Framework 4.5
Instalator .NET Framework 4.5 używa [Menedżera ponownego uruchamiania,](/windows/win32/rstmgr/about-restart-manager) aby zapobiec ponownemu uruchomieniu systemu, gdy tylko jest to możliwe podczas instalacji. Jeśli program instalacyjny aplikacji instaluje program .NET Framework, może połączyć się z Menedżerem ponownego uruchamiania, aby skorzystać z tej funkcji. Aby uzyskać więcej informacji, zobacz [Jak: Uzyskaj postęp z instalatora .NET Framework 4.5](how-to-get-progress-from-the-dotnet-installer.md).  
  
## <a name="reasons-for-a-restart"></a>Powody ponownego uruchomienia  
 Instalacja programu .NET Framework 4.5 wymaga ponownego uruchomienia systemu, jeśli aplikacja .NET Framework 4 jest używana podczas instalacji. Dzieje się tak, ponieważ program .NET Framework 4.5 zastępuje pliki .NET Framework 4 i wymaga, aby te pliki były dostępne podczas instalacji. W wielu przypadkach można zapobiec ponownemu uruchomieniu przez prewktuwizowane wykrywanie i closing.NET aplikacje Framework 4, które są w użyciu. Jednak niektóre aplikacje systemowe nie powinny być zamknięte. W takich przypadkach nie można uniknąć ponownego uruchomienia.  
  
## <a name="end-user-experience"></a>Środowisko użytkownika końcowego  
 Użytkownik końcowy, który wykonuje pełną instalację programu .NET Framework 4.5, ma możliwość uniknięcia ponownego uruchomienia systemu, jeśli instalator wykryje używane aplikacje .NET Framework 4. Komunikat zawiera listę wszystkich uruchomionych aplikacji .NET Framework 4 i udostępnia opcję zamknięcia tych aplikacji przed instalacją. Jeśli użytkownik potwierdzi, te aplikacje są zamykane przez instalatora i unika się ponownego uruchamiania systemu. Jeśli użytkownik nie odpowiada na wiadomość w określonym czasie, instalacja jest kontynuowana bez zamykania żadnych aplikacji.  
  
 Jeśli Menedżer ponownego uruchamiania wykryje sytuację, która będzie wymagać ponownego uruchomienia systemu, nawet jeśli uruchomione aplikacje są zamknięte, komunikat nie jest wyświetlany.  
  
 ![Okno dialogowe Zamknij aplikację z listą aktualnie uruchomionych programów.](./media/reducing-system-restarts/close-application-dialog.png)  
  
## <a name="using-a-chained-installer"></a>Korzystanie z instalatora łańcuchowego  
 Jeśli chcesz redystrybuować program .NET Framework z aplikacją, ale chcesz użyć własnego programu instalacyjnego i interfejsu użytkownika, możesz uwzględnić (łańcuch) proces instalacji programu .NET Framework do procesu instalacji. Aby uzyskać więcej informacji na temat instalacji łańcuchowych, zobacz [Przewodnik wdrażania dla deweloperów](deployment-guide-for-developers.md). Aby zmniejszyć liczbę ponownych uruchomień systemu w instalacjach łańcuchowych, instalator platformy .NET Framework dostarcza programowi instalacyjnemu listę aplikacji do zamknięcia. Program instalacyjny musi dostarczyć te informacje użytkownikowi za pośrednictwem interfejsu użytkownika, takiego jak okno komunikatu, uzyskać odpowiedź użytkownika, a następnie przekazać odpowiedź z powrotem do instalatora programu .NET Framework. Na przykład instalatora łańcuchowego zobacz artykuł [Jak: Pobierz postęp z instalatora .NET Framework 4.5](how-to-get-progress-from-the-dotnet-installer.md).  
  
 Jeśli używasz instalatora łańcuchowego, ale nie chcesz podać własnego okna komunikatów do zamykania aplikacji, możesz użyć opcji `/showrmui` i `/passive` opcji w wierszu polecenia podczas łańcucha procesu konfiguracji programu .NET Framework. Gdy używasz tych opcji razem, instalator pokazuje okno komunikatu do zamykania aplikacji, jeśli można je zamknąć, aby uniknąć ponownego uruchomienia systemu. To okno komunikatu zachowuje się tak samo w trybie pasywnym, jak w pełnym interfejsie użytkownika. Zobacz [Przewodnik wdrażania dla deweloperów,](deployment-guide-for-developers.md) aby uzyskać pełny zestaw opcji wiersza polecenia dla programu .NET Framework redystrybucyjnego.  
  
## <a name="see-also"></a>Zobacz też

- [Wdrożenie](index.md)
- [Przewodnik wdrażania dla deweloperów](deployment-guide-for-developers.md)
- [Porady: pobieranie danych o postępie z Instalatora .NET Framework 4.5](how-to-get-progress-from-the-dotnet-installer.md)
