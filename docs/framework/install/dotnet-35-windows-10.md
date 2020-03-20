---
title: Instalowanie programu .NET Framework 3.5 w systemie Windows 10, 8.1, 8
description: Dowiedz się, jak zainstalować program .NET Framework 3.5 w systemach Windows 10, Windows 8.1 i Windows 8.
ms.date: 07/16/2018
ms.openlocfilehash: cfe21c0821b8f3223301dcc802533e1aaf024a79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "76965948"
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a>Instalowanie programu .NET Framework 3.5 w systemie Windows 10, Windows 8.1 lub Windows 8

Do uruchomienia aplikacji w systemach Windows 10, Windows 8.1 i Windows 8 może być potrzebny program .NET Framework 3.5. Tych instrukcji można również użyć dla wcześniejszych wersji systemu Windows.

## <a name="download-the-offline-installer"></a>Pobierz instalator w trybie offline

Instalator trybu offline dodatku SP1 programu .NET Framework 3.5 jest dostępny na [stronie pobierania dodatku SP1 programu .NET Framework 3.5](https://dotnet.microsoft.com/download/dotnet-framework/net35-sp1) i jest dostępny dla wersji systemu Windows wcześniejszych niż Windows 10.

## <a name="install-the-net-framework-35-on-demand"></a>Instalowanie programu .NET Framework 3.5 na żądanie

Następujące okno dialogowe konfiguracji może zostać wyświetlone podczas próby uruchomienia aplikacji wymagającej programu .NET Framework 3.5. Wybierz **pozycję Zainstaluj tę funkcję,** aby włączyć program .NET Framework 3.5. Ta opcja wymaga połączenia z Internetem.

![Zrzut ekranu przedstawiający okno dialogowe instalacji programu .NET Framework.](./media/dotnet-35-windows-10/dotnet-framework-installation-dialog.png)

### <a name="why-am-i-getting-this-pop-up"></a>Dlaczego ogeneruję to wyskakujące okienko?

Program .NET Framework jest tworzony przez firmę Microsoft i zapewnia środowisko do uruchamiania aplikacji. Dostępne są różne wersje. Wiele firm rozwija swoje aplikacje do uruchamiania przy użyciu programu .NET Framework, a te aplikacje są przeznaczone dla określonej wersji. Jeśli widzisz to okno podręczne, próbujesz uruchomić aplikację, która wymaga programu .NET Framework w wersji 3.5, ale ta wersja nie jest zainstalowana w systemie.

## <a name="enable-the-net-framework-35-in-control-panel"></a>Włączanie programu .NET Framework 3.5 w Panelu sterowania

Program .NET Framework 3.5 można włączyć za pośrednictwem Panelu sterowania systemu Windows. Ta opcja wymaga połączenia z Internetem.

1. Naciśnij klawisz ![Windows Zrzut ekranu logo klucza systemu Windows.](./media/dotnet-35-windows-10/windows-keyboard-logo.png) na klawiaturze wpisz "Funkcje systemu Windows" i naciśnij klawisz Enter. Zostanie wyświetlone okno dialogowe **Włączanie lub wyłączanie funkcji systemu Windows.**

2. Zaznacz pole wyboru **.NET Framework 3.5 (w tym .NET 2.0 i 3.0),** wybierz **przycisk OK**i uruchom ponownie komputer, jeśli zostanie wyświetlony monit.

   ![Zrzut ekranu przedstawiający instalację platformy .NET za pomocą panelu sterowania.](./media/dotnet-35-windows-10/dotnet-control-panel.png)

   Nie trzeba wybierać elementów podrzędnych dla **Windows Communication Foundation (WCF) Http Activation** i Windows Communication Foundation **(WCF) Non-HTTP Activation ,chyba** że jesteś deweloperem lub administratorem serwera, który wymaga tej funkcji.

## <a name="troubleshoot-the-installation-of-the-net-framework-35"></a>Rozwiązywanie problemów z instalacją programu .NET Framework 3.5

Podczas instalacji może wystąpić błąd 0x800f0906, 0x800f0907, 0x800f081f lub 0x800F0922, w tym przypadku odnoszą się do [błędu instalacji .NET Framework 3.5: 0x800f0906, 0x800f0907 lub 0x800f081f,](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) aby zobaczyć, jak rozwiązać te problemy.

Jeśli nadal nie możesz rozwiązać problemu z instalacją lub nie masz połączenia internetowego, możesz spróbować zainstalować go przy użyciu nośnika instalacyjnego systemu Windows. Aby uzyskać więcej informacji, zobacz [Wdrażanie programu .NET Framework 3.5 przy użyciu obsługi obrazu wdrażania i zarządzania (DISM)](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism). Jeśli nie masz nośnika instalacyjnego, zobacz [Tworzenie nośnika instalacyjnego dla systemu Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).

> [!WARNING]
> Jeśli nie polegasz na usłudze Windows Update jako źródle instalacji programu .NET Framework 3.5, należy upewnić się, że należy ściśle używać źródeł z tej samej odpowiedniej wersji systemu operacyjnego Windows. Użycie ścieżki źródłowej, która nie odpowiada tej samej wersji systemu Windows, nie uniemożliwi zainstalowania niedopasowanej wersji programu .NET Framework 3.5. Spowoduje to jednak, że system będzie w stanie nieobsługiwanym i niesprawnym.
