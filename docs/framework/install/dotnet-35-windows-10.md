---
title: Instalowanie programu .NET Framework 3.5 w systemie Windows 10, Windows 8.1 i Windows 8
description: Dowiedz się, jak zainstalować program .NET Framework 3.5 w systemie Windows 10, Windows 8.1 i Windows 8.
author: rlander
ms.author: mairaw
ms.date: 07/16/2018
ms.openlocfilehash: 7b3b7ca5709008260ea284602a3ed8d2b288c410
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2018
ms.locfileid: "43257523"
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a>Instalowanie programu .NET Framework 3.5 w systemie Windows 10, Windows 8.1 i Windows 8

Uruchamianie aplikacji w systemie Windows 10, Windows 8.1 i Windows 8 w programie .NET Framework 3.5, może być konieczne. Umożliwia także te instrukcje dla wcześniejszych wersji Windows.

## <a name="install-the-net-framework-35-on-demand"></a>Instalowanie programu .NET Framework 3.5 na żądanie

Następujące okno dialogowe konfiguracji może zostać wyświetlony, jeśli zostanie podjęta próba uruchomienia aplikacji, która wymaga programu .NET Framework 3.5. Wybierz **Zainstaluj tę funkcję** Aby włączyć program .NET Framework 3.5. Ta opcja wymaga połączenia internetowego.

![.NET framework w instalacji w oknie dialogowym](./media/dotnet-framework-installation-dialog.jpg)

### <a name="why-am-i-getting-this-pop-up"></a>Dlaczego otrzymuję to wyskakujące?

.NET Framework jest tworzony przez firmę Microsoft i zapewnia środowisko do uruchamiania aplikacji. Dostępne są różne wersje. Wiele firm twórz swoje aplikacje do uruchamiania przy użyciu programu .NET Framework, a te aplikacje są przeznaczone dla określonej wersji. Jeśli zobaczysz to okno, próbuje uruchomić aplikację, która wymaga .NET Framework w wersji 3.5, ale ta wersja nie jest zainstalowany w systemie.

## <a name="enable-the-net-framework-35-in-control-panel"></a>Włączanie programu .NET Framework 3.5 w Panelu sterowania

Można włączyć program .NET Framework 3.5 za pomocą Panelu sterowania Windows. Ta opcja wymaga połączenia internetowego.

1. Naciśnij klawisz Windows, Windows ![Windows logo](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) na klawiaturze, wpisz "Windows funkcji", a następnie naciśnij klawisz Enter. **Windows Włącz lub wyłącz funkcje** pojawi się okno dialogowe.

2. Wybierz **.NET Framework 3.5 (w tym .NET 2.0 i 3.0)** pole wyboru, wybierz opcję **OK**i ponownie uruchomić komputer, jeśli zostanie wyświetlony monit.

   ![Instalowanie platformy .NET przy użyciu Panelu sterowania](./media/dotnet-control-panel.png)

   Nie ma potrzeby wybierania elementów podrzędnych dla **Aktywacja HTTP Windows Communication Foundation (WCF)** i **Aktywacja bez HTTP Windows Communication Foundation (WCF)** chyba, że jesteś deweloperem lub administrator serwera, który wymaga tej funkcji.

## <a name="troubleshoot-the-installation-of-the-net-framework-35"></a>Rozwiązywanie problemów z instalacją programu .NET Framework 3.5

Podczas instalacji, możesz napotkać błąd 0x800f0906, 0x800f0907, 0x800f081f lub 0x800F0922, w którym to przypadku odnoszą się do [błąd instalacji programu .NET Framework 3.5: 0x800f0906, 0x800f0907 lub 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) można zobaczyć, jak je rozwiązać problemy.

Jeśli nadal nie możesz rozwiązać problem z instalacją lub nie masz dostępu do Internetu, możesz spróbować zainstalować je przy użyciu nośnika instalacyjnego Windows. Aby uzyskać więcej informacji, zobacz [wdrażania .NET Framework 3.5 przy użyciu Deployment Image Servicing i zarządzanie (DISM)](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism). Jeśli nie masz na nośniku instalacyjnym, zobacz [Utwórz nośnik instalacyjny dla Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).

> [!WARNING]
> Jeśli nie jesteś jednostki uzależnionej w usłudze Windows Update jako źródła do instalowania programu .NET Framework 3.5, należy używać źródła z tej samej odpowiedniej wersji systemu operacyjnego Windows. Przy użyciu ścieżki źródłowej, która nie jest zgodny z tej samej wersji systemu Windows nie będzie zapobiec instalowanego niezgodną wersję programu .NET Framework 3.5. Jednak to spowoduje, że system będzie w stanie nieobsługiwane i niezdatny do użytku.
