---
title: Zainstaluj program .NET Framework 3.5 w systemie Windows 10, Windows 8.1 i Windows 8
description: Dowiedz się, jak zainstalować program .NET Framework 3.5 w systemie Windows 10, Windows 8.1 i Windows 8.
author: rlander
ms.author: mairaw
ms.date: 03/30/2018
ms.openlocfilehash: 226449b8ee7c9360e6bfdc5bfa5dfeb59f19bd2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33387419"
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a>Zainstaluj program .NET Framework 3.5 w systemie Windows 10, Windows 8.1 i Windows 8

Uruchamianie aplikacji w systemie Windows 10, Windows 8.1 i Windows 8 w programie .NET Framework 3.5 może być konieczne. Umożliwia także te instrukcje dla wcześniejszych wersji systemu Windows.

## <a name="install-the-net-framework-35-on-demand"></a>Zainstaluj program .NET Framework 3.5 na żądanie

Następujące okna dialogowego konfiguracji może być wyświetlana, jeśli zostanie podjęta próba uruchomienia aplikacji, która wymaga programu .NET Framework 3.5. Wybierz **Zainstaluj tę funkcję** Aby włączyć program .NET Framework 3.5. Ta opcja wymaga połączenia internetowego.

![Okno instalacji programu .NET framework](./media/dotnet-framework-installation-dialog.jpg)

### <a name="why-am-i-getting-this-pop-up"></a>Dlaczego otrzymuję to wyskakujące?

.NET Framework jest tworzony przez firmę Microsoft i udostępnia środowisko uruchamiania aplikacji. Dostępne są różne wersje. Wiele firm opracowywanie aplikacji przy użyciu programu .NET Framework, a te aplikacje docelowe określonej wersji. Jeśli to okno jest wyświetlane, próbuje uruchomić aplikację, która wymaga programu .NET Framework w wersji 3.5, ale ta wersja nie jest zainstalowany w systemie.

## <a name="enable-the-net-framework-35-in-control-panel"></a>Włączanie programu .NET Framework 3.5 w Panelu sterowania

Można włączyć program .NET Framework 3.5 za pomocą Panelu sterowania systemu Windows. Ta opcja wymaga połączenia internetowego.

1. Naciśnij klawisz systemu Windows, Windows ![logo systemu Windows](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) na klawiaturze, wpisz "Funkcje systemu Windows", a następnie naciśnij klawisz Enter. **Włącz lub wyłącz funkcje systemu Windows** zostanie wyświetlone okno dialogowe.

2. Wybierz **.NET Framework 3.5 (w tym .NET 2.0 i 3.0)** zaznacz pole wyboru **OK**i uruchom ponownie komputer, jeśli zostanie wyświetlony monit.

   ![Zainstaluj oprogramowanie .NET w Panelu sterowania](./media/dotnet-control-panel.png)

   Nie musisz wybrać elementy podrzędne dla **Aktywacja HTTP usług Windows Communication Foundation (WCF)** i **Aktywacja bez HTTP Windows Communication Foundation (WCF)** Jeśli nie jesteś deweloperem lub administrator serwera, który wymaga tej funkcji.

## <a name="troubleshoot-the-installation-of-the-net-framework-35"></a>Rozwiązywanie problemów z instalacją programu .NET Framework 3.5

Podczas instalacji, może wystąpić błąd 0x800f0906, 0x800f0907, 0x800f081f lub 0x800F0922, w którym to przypadku odwoływać się do [błąd instalacji programu .NET Framework 3.5: 0x800f0906, 0x800f0907 lub 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) na temat sposobu rozwiązania tych problemy.

Jeśli nadal nie możesz rozwiązać problemu z instalacją lub nie masz dostępu do Internetu, możesz spróbować zainstalować go za pomocą nośnika instalacyjnego systemu Windows. Aby uzyskać więcej informacji, zobacz [wdrożyć program .NET Framework 3.5 przy użyciu Deployment Image Servicing and Management (DISM)](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism). Jeśli nie masz nośnika instalacyjnego, zobacz [Utwórz nośnik instalacyjny dla systemu Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).
