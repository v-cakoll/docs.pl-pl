---
title: Zainstaluj program .NET Framework 3.5 w systemie Windows 10, Windows 8.1 i Windows 8
description: "Dowiedz się, jak zainstalować program .NET Framework 3.5 w systemie Windows 10, Windows 8.1 i Windows 8."
author: rlander
ms.author: mairaw
ms.date: 11/27/2017
ms.topic: article
ms.prod: .net-framework
ms.workload: dotnet
ms.openlocfilehash: ca56bfb37cee60ab014dada7b5d72b74b375dd7f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a>Zainstaluj program .NET Framework 3.5 w systemie Windows 10, Windows 8.1 i Windows 8

Uruchamianie aplikacji w systemie Windows 10, Windows 8.1 i Windows 8 w programie .NET Framework 3.5 może być konieczne. Umożliwia także te instrukcje dla wcześniejszych wersji systemu Windows.

## <a name="install-the-net-framework-35-on-demand"></a>Zainstaluj program .NET Framework 3.5 na żądanie

Następujące okna dialogowego konfiguracji może być wyświetlana, jeśli zostanie podjęta próba uruchomienia aplikacji, która wymaga programu .NET Framework 3.5. Wybierz **Zainstaluj tę funkcję** Aby włączyć program .NET Framework 3.5. Ta opcja wymaga połączenia internetowego.

![Okno instalacji programu .NET framework](./media/dotnet-framework-installation-dialog.jpg)

## <a name="enable-the-net-framework-35-in-control-panel"></a>Włączanie programu .NET Framework 3.5 w Panelu sterowania

Można włączyć program .NET Framework 3.5 za pomocą Panelu sterowania systemu Windows. Ta opcja wymaga połączenia internetowego.

1. Naciśnij klawisz systemu Windows, Windows ![logo systemu Windows](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) na klawiaturze, wpisz "Funkcje systemu Windows", a następnie naciśnij klawisz Enter. **Włącz lub wyłącz funkcje systemu Windows** zostanie wyświetlone okno dialogowe.

2. Wybierz **.NET Framework 3.5 (w tym .NET 2.0 i 3.0)** zaznacz pole wyboru **OK**i uruchom ponownie komputer, jeśli zostanie wyświetlony monit.

   ![Zainstaluj oprogramowanie .NET w Panelu sterowania](./media/dotnet-control-panel.png)

   Nie musisz wybrać elementy podrzędne dla **Aktywacja HTTP usług Windows Communication Foundation (WCF)** i **Aktywacja bez HTTP Windows Communication Foundation (WCF)** Jeśli nie jesteś deweloperem lub administrator serwera, który wymaga tej funkcji.

## <a name="troubleshoot-the-installation-of-the-net-framework-35"></a>Rozwiązywanie problemów z instalacją programu .NET Framework 3.5

Podczas instalacji, może wystąpić błąd 0x800f0906, 0x800f0907, 0x800f081f lub 0x800F0922, w którym to przypadku odwoływać się do [błąd instalacji programu .NET Framework 3.5: 0x800f0906, 0x800f0907 lub 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) na temat sposobu rozwiązania tych problemy.

Jeśli nie wszystkie metody omówione w poprzednim artykule, lub jeśli nie masz połączenia internetowego jest niezbędne do korzystania z nośnika instalacyjnego systemu Windows. Aby uzyskać więcej informacji, zobacz [wdrożyć program .NET Framework 3.5 przy użyciu Deployment Image Servicing and Management (DISM)](https://technet.microsoft.com/library/Dn482069.aspx). Jeśli nie masz nośnika instalacyjnego, zobacz [Utwórz nośnik instalacyjny dla systemu Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).