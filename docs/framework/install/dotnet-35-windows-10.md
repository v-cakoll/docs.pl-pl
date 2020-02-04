---
title: Zainstaluj .NET Framework 3,5 w systemie Windows 10, 8,1, 8
description: Dowiedz się, jak zainstalować .NET Framework 3,5 w systemie Windows 10, Windows 8.1 i Windows 8.
ms.date: 07/16/2018
ms.openlocfilehash: cfe21c0821b8f3223301dcc802533e1aaf024a79
ms.sourcegitcommit: feb42222f1430ca7b8115ae45e7a38fc4a1ba623
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/02/2020
ms.locfileid: "76965948"
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a>Instalowanie programu .NET Framework 3.5 w systemie Windows 10, Windows 8.1 lub Windows 8

Aby uruchomić aplikację w systemie Windows 10, Windows 8.1 i Windows 8, może być konieczne .NET Framework 3,5. Możesz również użyć tych instrukcji dla wcześniejszych wersji systemu Windows.

## <a name="download-the-offline-installer"></a>Pobierz instalatora w trybie offline

Instalator offline programu .NET Framework 3,5 z dodatkiem SP1 jest dostępny na [stronie pobierania .NET Framework 3,5 SP1](https://dotnet.microsoft.com/download/dotnet-framework/net35-sp1) i jest dostępny dla wersji systemu Windows starszych niż Windows 10.

## <a name="install-the-net-framework-35-on-demand"></a>Instalowanie .NET Framework 3,5 na żądanie

Jeśli spróbujesz uruchomić aplikację, która wymaga .NET Framework 3,5, może zostać wyświetlone następujące okno dialogowe konfiguracji. Wybierz pozycję **Zainstaluj tę funkcję** , aby włączyć .NET Framework 3,5. Ta opcja wymaga połączenia internetowego.

![Zrzut ekranu przedstawiający okno dialogowe instalacji .NET Framework.](./media/dotnet-35-windows-10/dotnet-framework-installation-dialog.png)

### <a name="why-am-i-getting-this-pop-up"></a>Dlaczego otrzymuję ten wyskakujące okienko?

.NET Framework jest tworzony przez firmę Microsoft i udostępnia środowisko do uruchamiania aplikacji. Dostępne są różne wersje. Wiele firm opracowuje aplikacje do uruchamiania przy użyciu .NET Framework i aplikacje te są przeznaczone dla konkretnej wersji. Jeśli zobaczysz to okno podręczne, próbujesz uruchomić aplikację, która wymaga .NET Framework w wersji 3,5, ale ta wersja nie jest zainstalowana w systemie.

## <a name="enable-the-net-framework-35-in-control-panel"></a>Włączanie .NET Framework 3,5 w panelu sterowania

.NET Framework 3,5 można włączyć za pomocą panelu sterowania systemu Windows. Ta opcja wymaga połączenia internetowego.

1. Naciśnij zrzut ekranu ![klucza systemu Windows w logo klucza systemu Windows.](./media/dotnet-35-windows-10/windows-keyboard-logo.png) na klawiaturze wpisz "funkcje systemu Windows", a następnie naciśnij klawisz ENTER. Zostanie wyświetlone okno dialogowe **Włączanie lub wyłączanie funkcji systemu Windows** .

2. Zaznacz pole wyboru **.NET Framework 3,5 (zawiera .net 2,0 i 3,0)** , wybierz **przycisk OK**, a następnie uruchom ponownie komputer po wyświetleniu monitu.

   ![Zrzut ekranu przedstawiający instalację platformy .NET przy użyciu panelu sterowania.](./media/dotnet-35-windows-10/dotnet-control-panel.png)

   Nie musisz wybierać elementów podrzędnych dla **Windows Communication Foundation (WCF) Aktywacja HTTP** i **Windows Communication Foundation (WCF) Aktywacja bez http** , chyba że jesteś deweloperem lub administratorem serwera, który wymaga tej funkcji.

## <a name="troubleshoot-the-installation-of-the-net-framework-35"></a>Rozwiązywanie problemów z instalacją .NET Framework 3,5

Podczas instalacji może wystąpić błąd 0x800f0906, 0x800f0907, 0x800F081F lub 0x800F0922, a w tym przypadku wystąpił [błąd instalacji .NET Framework 3,5:0x800f0906, 0x800f0907 lub 0x800F081F](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) , aby zobaczyć, jak rozwiązać te problemy.

Jeśli nadal nie możesz rozwiązać problemu z instalacją lub nie masz połączenia z Internetem, możesz spróbować go zainstalować przy użyciu nośnika instalacyjnego systemu Windows. Aby uzyskać więcej informacji, zobacz [wdrażanie .NET Framework 3,5 przy użyciu narzędzia do obsługi i zarządzania obrazami wdrażania (DISM)](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism). Jeśli nie masz nośnika instalacyjnego, zobacz [Tworzenie nośnika instalacyjnego dla systemu Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).

> [!WARNING]
> Jeśli nie korzystasz z Windows Update jako źródła do zainstalowania .NET Framework 3,5, musisz upewnić się, że źródła są używane z tej samej wersji systemu operacyjnego Windows. Użycie ścieżki źródłowej, która nie jest zgodna z tą samą wersją systemu Windows, nie uniemożliwi instalacji niezgodnej wersji .NET Framework 3,5. Spowoduje to jednak, że system będzie w stanie nieobsługiwanym i nieobsługowym.
