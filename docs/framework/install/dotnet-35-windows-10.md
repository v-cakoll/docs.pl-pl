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
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a><span data-ttu-id="68def-104">Zainstaluj program .NET Framework 3.5 w systemie Windows 10, Windows 8.1 i Windows 8</span><span class="sxs-lookup"><span data-stu-id="68def-104">Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8</span></span>

<span data-ttu-id="68def-105">Uruchamianie aplikacji w systemie Windows 10, Windows 8.1 i Windows 8 w programie .NET Framework 3.5 może być konieczne.</span><span class="sxs-lookup"><span data-stu-id="68def-105">You may need the .NET Framework 3.5 to run an app on Windows 10, Windows 8.1, and Windows 8.</span></span> <span data-ttu-id="68def-106">Umożliwia także te instrukcje dla wcześniejszych wersji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="68def-106">You can also use these instructions for earlier Windows versions.</span></span>

## <a name="install-the-net-framework-35-on-demand"></a><span data-ttu-id="68def-107">Zainstaluj program .NET Framework 3.5 na żądanie</span><span class="sxs-lookup"><span data-stu-id="68def-107">Install the .NET Framework 3.5 on Demand</span></span>

<span data-ttu-id="68def-108">Następujące okna dialogowego konfiguracji może być wyświetlana, jeśli zostanie podjęta próba uruchomienia aplikacji, która wymaga programu .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="68def-108">You may see the following configuration dialog if you try to run an app that requires the .NET Framework 3.5.</span></span> <span data-ttu-id="68def-109">Wybierz **Zainstaluj tę funkcję** Aby włączyć program .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="68def-109">Choose **Install this feature** to enable the .NET Framework 3.5.</span></span> <span data-ttu-id="68def-110">Ta opcja wymaga połączenia internetowego.</span><span class="sxs-lookup"><span data-stu-id="68def-110">This option requires an Internet connection.</span></span>

![Okno instalacji programu .NET framework](./media/dotnet-framework-installation-dialog.jpg)

## <a name="enable-the-net-framework-35-in-control-panel"></a><span data-ttu-id="68def-112">Włączanie programu .NET Framework 3.5 w Panelu sterowania</span><span class="sxs-lookup"><span data-stu-id="68def-112">Enable the .NET Framework 3.5 in Control Panel</span></span>

<span data-ttu-id="68def-113">Można włączyć program .NET Framework 3.5 za pomocą Panelu sterowania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="68def-113">You can enable the .NET Framework 3.5 through the Windows Control Panel.</span></span> <span data-ttu-id="68def-114">Ta opcja wymaga połączenia internetowego.</span><span class="sxs-lookup"><span data-stu-id="68def-114">This option requires an Internet connection.</span></span>

1. <span data-ttu-id="68def-115">Naciśnij klawisz systemu Windows, Windows ![logo systemu Windows](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) na klawiaturze, wpisz "Funkcje systemu Windows", a następnie naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="68def-115">Press the Windows key Windows ![Windows logo](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) on your keyboard, type "Windows Features", and press Enter.</span></span> <span data-ttu-id="68def-116">**Włącz lub wyłącz funkcje systemu Windows** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="68def-116">The **Turn Windows features on or off** dialog box appears.</span></span>

2. <span data-ttu-id="68def-117">Wybierz **.NET Framework 3.5 (w tym .NET 2.0 i 3.0)** zaznacz pole wyboru **OK**i uruchom ponownie komputer, jeśli zostanie wyświetlony monit.</span><span class="sxs-lookup"><span data-stu-id="68def-117">Select the **.NET Framework 3.5 (includes .NET 2.0 and 3.0)** check box, select **OK**, and reboot your computer if prompted.</span></span>

   ![Zainstaluj oprogramowanie .NET w Panelu sterowania](./media/dotnet-control-panel.png)

   <span data-ttu-id="68def-119">Nie musisz wybrać elementy podrzędne dla **Aktywacja HTTP usług Windows Communication Foundation (WCF)** i **Aktywacja bez HTTP Windows Communication Foundation (WCF)** Jeśli nie jesteś deweloperem lub administrator serwera, który wymaga tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="68def-119">You don't need to select the child items for **Windows Communication Foundation (WCF) HTTP Activation** and **Windows Communication Foundation (WCF) Non-HTTP Activation** unless you're a developer or server administrator who requires this functionality.</span></span>
