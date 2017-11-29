---
title: Zainstaluj program .NET Framework 3.5 w systemie Windows 10, Windows 8.1 i Windows 8
description: "Dowiedz się, jak zainstalować program .NET Framework 3.5 w systemie Windows 10, Windows 8.1 i Windows 8."
author: rlander
ms.author: mairaw
keywords: .NET framework, instalacja
ms.date: 05/26/2017
ms.topic: article
ms.prod: .net-framework
ms.technology: vs-ide-deployment
ms.devlang: dotnet
ms.assetid: 67cda1d5-c6g4-4eb5-93e6-4f478de07ff7
ms.openlocfilehash: 85a3cada074714c24015d90c26d94551f4f411f2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
