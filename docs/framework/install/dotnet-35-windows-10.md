---
title: Zainstaluj program .NET Framework 3.5 w systemie Windows 10, Windows 8.1 i Windows 8
description: Dowiedz się, jak zainstalować program .NET Framework 3.5 w systemie Windows 10, Windows 8.1 i Windows 8.
author: rlander
ms.author: mairaw
ms.date: 03/30/2018
ms.topic: article
ms.prod: .net-framework
ms.workload:
- dotnet
ms.openlocfilehash: 09c4f81da76bb6608c3e579c442cf686ffab1688
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a><span data-ttu-id="819a6-103">Zainstaluj program .NET Framework 3.5 w systemie Windows 10, Windows 8.1 i Windows 8</span><span class="sxs-lookup"><span data-stu-id="819a6-103">Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8</span></span>

<span data-ttu-id="819a6-104">Uruchamianie aplikacji w systemie Windows 10, Windows 8.1 i Windows 8 w programie .NET Framework 3.5 może być konieczne.</span><span class="sxs-lookup"><span data-stu-id="819a6-104">You may need the .NET Framework 3.5 to run an app on Windows 10, Windows 8.1, and Windows 8.</span></span> <span data-ttu-id="819a6-105">Umożliwia także te instrukcje dla wcześniejszych wersji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="819a6-105">You can also use these instructions for earlier Windows versions.</span></span>

## <a name="install-the-net-framework-35-on-demand"></a><span data-ttu-id="819a6-106">Zainstaluj program .NET Framework 3.5 na żądanie</span><span class="sxs-lookup"><span data-stu-id="819a6-106">Install the .NET Framework 3.5 on Demand</span></span>

<span data-ttu-id="819a6-107">Następujące okna dialogowego konfiguracji może być wyświetlana, jeśli zostanie podjęta próba uruchomienia aplikacji, która wymaga programu .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="819a6-107">You may see the following configuration dialog if you try to run an app that requires the .NET Framework 3.5.</span></span> <span data-ttu-id="819a6-108">Wybierz **Zainstaluj tę funkcję** Aby włączyć program .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="819a6-108">Choose **Install this feature** to enable the .NET Framework 3.5.</span></span> <span data-ttu-id="819a6-109">Ta opcja wymaga połączenia internetowego.</span><span class="sxs-lookup"><span data-stu-id="819a6-109">This option requires an Internet connection.</span></span>

![Okno instalacji programu .NET framework](./media/dotnet-framework-installation-dialog.jpg)

### <a name="why-am-i-getting-this-pop-up"></a><span data-ttu-id="819a6-111">Dlaczego otrzymuję to wyskakujące?</span><span class="sxs-lookup"><span data-stu-id="819a6-111">Why am I getting this pop-up?</span></span>

<span data-ttu-id="819a6-112">.NET Framework jest tworzony przez firmę Microsoft i udostępnia środowisko uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="819a6-112">The .NET Framework is created by Microsoft and provides an environment for running applications.</span></span> <span data-ttu-id="819a6-113">Dostępne są różne wersje.</span><span class="sxs-lookup"><span data-stu-id="819a6-113">There are different versions available.</span></span> <span data-ttu-id="819a6-114">Wiele firm opracowywanie aplikacji przy użyciu programu .NET Framework, a te aplikacje docelowe określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="819a6-114">Many companies develop their apps to run using the .NET Framework, and these apps target a specific version.</span></span> <span data-ttu-id="819a6-115">Jeśli to okno jest wyświetlane, próbuje uruchomić aplikację, która wymaga programu .NET Framework w wersji 3.5, ale ta wersja nie jest zainstalowany w systemie.</span><span class="sxs-lookup"><span data-stu-id="819a6-115">If you see this pop-up, you're trying to run an application that requires the .NET Framework version 3.5, but that version is not installed on your system.</span></span>

## <a name="enable-the-net-framework-35-in-control-panel"></a><span data-ttu-id="819a6-116">Włączanie programu .NET Framework 3.5 w Panelu sterowania</span><span class="sxs-lookup"><span data-stu-id="819a6-116">Enable the .NET Framework 3.5 in Control Panel</span></span>

<span data-ttu-id="819a6-117">Można włączyć program .NET Framework 3.5 za pomocą Panelu sterowania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="819a6-117">You can enable the .NET Framework 3.5 through the Windows Control Panel.</span></span> <span data-ttu-id="819a6-118">Ta opcja wymaga połączenia internetowego.</span><span class="sxs-lookup"><span data-stu-id="819a6-118">This option requires an Internet connection.</span></span>

1. <span data-ttu-id="819a6-119">Naciśnij klawisz systemu Windows, Windows ![logo systemu Windows](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) na klawiaturze, wpisz "Funkcje systemu Windows", a następnie naciśnij klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="819a6-119">Press the Windows key Windows ![Windows logo](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) on your keyboard, type "Windows Features", and press Enter.</span></span> <span data-ttu-id="819a6-120">**Włącz lub wyłącz funkcje systemu Windows** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="819a6-120">The **Turn Windows features on or off** dialog box appears.</span></span>

2. <span data-ttu-id="819a6-121">Wybierz **.NET Framework 3.5 (w tym .NET 2.0 i 3.0)** zaznacz pole wyboru **OK**i uruchom ponownie komputer, jeśli zostanie wyświetlony monit.</span><span class="sxs-lookup"><span data-stu-id="819a6-121">Select the **.NET Framework 3.5 (includes .NET 2.0 and 3.0)** check box, select **OK**, and reboot your computer if prompted.</span></span>

   ![Zainstaluj oprogramowanie .NET w Panelu sterowania](./media/dotnet-control-panel.png)

   <span data-ttu-id="819a6-123">Nie musisz wybrać elementy podrzędne dla **Aktywacja HTTP usług Windows Communication Foundation (WCF)** i **Aktywacja bez HTTP Windows Communication Foundation (WCF)** Jeśli nie jesteś deweloperem lub administrator serwera, który wymaga tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="819a6-123">You don't need to select the child items for **Windows Communication Foundation (WCF) HTTP Activation** and **Windows Communication Foundation (WCF) Non-HTTP Activation** unless you're a developer or server administrator who requires this functionality.</span></span>

## <a name="troubleshoot-the-installation-of-the-net-framework-35"></a><span data-ttu-id="819a6-124">Rozwiązywanie problemów z instalacją programu .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="819a6-124">Troubleshoot the installation of the .NET Framework 3.5</span></span>

<span data-ttu-id="819a6-125">Podczas instalacji, może wystąpić błąd 0x800f0906, 0x800f0907, 0x800f081f lub 0x800F0922, w którym to przypadku odwoływać się do [błąd instalacji programu .NET Framework 3.5: 0x800f0906, 0x800f0907 lub 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) na temat sposobu rozwiązania tych problemy.</span><span class="sxs-lookup"><span data-stu-id="819a6-125">During installation, you may encounter error 0x800f0906, 0x800f0907, 0x800f081f, or 0x800F0922, in which case refer to [.NET Framework 3.5 installation error: 0x800f0906, 0x800f0907, or 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) to see how to resolve these issues.</span></span>

<span data-ttu-id="819a6-126">Jeśli nadal nie możesz rozwiązać problemu z instalacją lub nie masz dostępu do Internetu, możesz spróbować zainstalować go za pomocą nośnika instalacyjnego systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="819a6-126">If you still can't resolve your installation issue or you don't have an Internet connection, you can try installing it using your Windows installation media.</span></span> <span data-ttu-id="819a6-127">Aby uzyskać więcej informacji, zobacz [wdrożyć program .NET Framework 3.5 przy użyciu Deployment Image Servicing and Management (DISM)](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism).</span><span class="sxs-lookup"><span data-stu-id="819a6-127">For more information, see [Deploy .NET Framework 3.5 by using Deployment Image Servicing and Management (DISM)](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism).</span></span> <span data-ttu-id="819a6-128">Jeśli nie masz nośnika instalacyjnego, zobacz [Utwórz nośnik instalacyjny dla systemu Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).</span><span class="sxs-lookup"><span data-stu-id="819a6-128">If you don't have the installation media, see [Create installation media for Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).</span></span>
