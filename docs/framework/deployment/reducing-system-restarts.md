---
title: Zmniejszenie liczby ponownych uruchomień systemu podczas instalowania programu .NET Framework 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework, reducing system restarts
- installing .NET Framework
- installation [.NET Framework]
ms.assetid: 7aa8cb72-dee9-4716-ac54-b17b9ae8218f
ms.openlocfilehash: 6261a883e7b99b7fd38da2a17ab4820c81552506
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716429"
---
# <a name="reducing-system-restarts-during-net-framework-45-installations"></a>Zmniejszenie liczby ponownych uruchomień systemu podczas instalowania programu .NET Framework 4.5
Instalator .NET Framework 4,5 korzysta z [Menedżera ponownego uruchamiania](/windows/win32/rstmgr/about-restart-manager) , aby zapobiec ponownemu uruchamianiu systemu, gdy jest to możliwe podczas instalacji. Jeśli program instalacyjny aplikacji zainstaluje .NET Framework, może to zrobić za pomocą Menedżera ponownego uruchamiania, aby skorzystać z tej funkcji. Aby uzyskać więcej informacji, zobacz [jak to zrobić: pobieranie postępu z instalatora .NET Framework 4,5](how-to-get-progress-from-the-dotnet-installer.md).  
  
## <a name="reasons-for-a-restart"></a>Przyczyny ponownego uruchomienia  
 Instalacja .NET Framework 4,5 wymaga ponownego uruchomienia systemu, jeśli aplikacja .NET Framework 4 jest używana podczas instalacji. Wynika to z faktu, że .NET Framework 4,5 zastępuje pliki .NET Framework 4 i wymaga, aby te pliki były dostępne podczas instalacji. W wielu przypadkach ponowne uruchomienie może być uniemożliwione przez zapobiegawczo wykrywanie i closing.NET aplikacji Framework 4, które są używane. Niektóre aplikacje systemowe nie powinny jednak być zamknięte. W takich przypadkach nie można uniknąć ponownego uruchomienia.  
  
## <a name="end-user-experience"></a>Środowisko użytkownika końcowego  
 Użytkownik końcowy, który wykonuje pełną instalację .NET Framework 4,5, ma możliwość uniknięcia ponownego uruchomienia systemu, jeśli Instalator wykryje aplikacje .NET Framework 4 w użyciu. Komunikat zawiera wszystkie uruchomione .NET Framework 4 aplikacje i udostępnia opcję zamykania tych aplikacji przed instalacją. Jeśli użytkownik potwierdzi, te aplikacje są zamykane przez Instalatora, a ponowne uruchomienie systemu jest możliwe. Jeśli użytkownik nie odpowie na komunikat w określonym czasie, instalacja będzie kontynuowana bez zamykania aplikacji.  
  
 Jeśli Menedżer ponownego uruchamiania wykryje sytuację, która będzie wymagała ponownego uruchomienia systemu, nawet jeśli uruchomione aplikacje są zamknięte, komunikat nie zostanie wyświetlony.  
  
 ![Okno dialogowe Zamykanie aplikacji wyświetla listę aktualnie uruchomionych programów.](./media/reducing-system-restarts/close-application-dialog.png)  
  
## <a name="using-a-chained-installer"></a>Używanie Instalatora łańcucha  
 Jeśli chcesz ponownie rozpowszechnić .NET Framework z aplikacją, ale chcesz użyć własnego programu instalacyjnego i interfejsu użytkownika, możesz dołączyć proces instalacji .NET Framework (łańcucha) do procesu instalacji. Aby uzyskać więcej informacji na temat instalacji łańcuchowych, zobacz [Przewodnik wdrażania dla deweloperów](deployment-guide-for-developers.md). Aby zmniejszyć liczbę ponownych uruchomień systemu w instalacjach łańcucha, Instalator .NET Framework dostarcza program instalacyjny z listą aplikacji do zamknięcia. Program instalacyjny musi przekazać użytkownikowi te informacje za pomocą interfejsu użytkownika, takiego jak okno komunikatu, uzyskać odpowiedzi użytkownika, a następnie przekazać odpowiedź z powrotem do Instalatora .NET Framework. Aby zapoznać się z przykładem Instalatora łańcucha, zobacz artykuł [jak: pobieranie postępu z instalatora .NET Framework 4,5](how-to-get-progress-from-the-dotnet-installer.md).  
  
 Jeśli używasz instalatora łańcucha, ale nie chcesz podawać własnego okna komunikatów do zamykania aplikacji, możesz użyć opcji `/showrmui` i `/passive` w wierszu polecenia podczas łańcucha procesu instalacji .NET Framework. Jeśli te opcje są używane razem, Instalator wyświetli okno komunikatu dotyczące zamykania aplikacji, jeśli można je zamknąć, aby uniknąć ponownego uruchomienia systemu. To okno komunikatu działa tak samo w trybie pasywnym, jak w przypadku pełnego interfejsu użytkownika. Aby uzyskać pełny zestaw opcji wiersza polecenia dla pakietu redystrybucyjnego .NET Framework, zobacz [Przewodnik wdrażania dla deweloperów](deployment-guide-for-developers.md) .  
  
## <a name="see-also"></a>Zobacz także

- [Wdrażanie](index.md)
- [Przewodnik wdrażania dla deweloperów](deployment-guide-for-developers.md)
- [Instrukcje: Pobieranie danych o postępie z Instalatora .NET Framework 4.5](how-to-get-progress-from-the-dotnet-installer.md)
