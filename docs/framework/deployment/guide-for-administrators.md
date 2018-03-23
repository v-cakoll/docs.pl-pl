---
title: .NET Framework — Przewodnik wdrażania dla administratorów
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
caps.latest.revision: ''
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f57b5db5c03030d8cb930355586d0253cae13319
ms.sourcegitcommit: 6f967c86dde55472440f0c8669b0e910ee3c53ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="net-framework-deployment-guide-for-administrators"></a><span data-ttu-id="015f2-102">.NET Framework — Przewodnik wdrażania dla administratorów</span><span class="sxs-lookup"><span data-stu-id="015f2-102">.NET Framework Deployment Guide for Administrators</span></span>
<span data-ttu-id="015f2-103">W tym artykule opisano, jak administrator systemu może wdrożyć [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] i jego zależności systemu przez sieć przy użyciu programu Microsoft System Center Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="015f2-103">This step-by-step article describes how a system administrator can deploy the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] and its system dependencies across a network by using Microsoft System Center Configuration Manager.</span></span> <span data-ttu-id="015f2-104">W tym artykule przyjęto założenie, że wszystkie docelowe komputery klienckie spełniają minimalne wymagania programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="015f2-104">This article assumes that all target client computers meet the minimum requirements for the .NET Framework.</span></span> <span data-ttu-id="015f2-105">Aby uzyskać listę wymagania sprzętowe i programowe instalacji [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], zobacz [wymagania systemowe](../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="015f2-105">For a list of the software and hardware requirements for installing the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], see [System Requirements](../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="015f2-106">Oprogramowania wymienione w niniejszym dokumencie, w tym bez ograniczeń, [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], System Center Configuration Manager i usługi Active Directory, jest każda zgodnie z postanowieniami licencyjnymi.</span><span class="sxs-lookup"><span data-stu-id="015f2-106">The software referenced in this document, including, without limitation, the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], System Center Configuration Manager, and Active Directory, are each subject to license terms and conditions.</span></span> <span data-ttu-id="015f2-107">W tych instrukcjach przyjęto założenie, że takie postanowienia licencyjne i warunki zostały przejrzane i zaakceptowane przez właściwych licencjobiorców oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="015f2-107">These instructions assume that such license terms and conditions have been reviewed and accepted by the appropriate licensees of the software.</span></span> <span data-ttu-id="015f2-108">Te instrukcje nie unieważniają żadnego postanowienia tych umów licencyjnych.</span><span class="sxs-lookup"><span data-stu-id="015f2-108">These instructions do not waive any of the terms and conditions of such license agreements.</span></span>  
>   
>  <span data-ttu-id="015f2-109">Aby uzyskać informacje o pomocy technicznej dla programu .NET Framework, zobacz [obsługuje zasady cyklu pomocy firmy Microsoft .NET Framework](http://go.microsoft.com/fwlink/?LinkId=196607) w witrynie sieci Web Microsoft Support.</span><span class="sxs-lookup"><span data-stu-id="015f2-109">For information about support for the .NET Framework, see [Microsoft .NET Framework Support Lifecycle Policy](http://go.microsoft.com/fwlink/?LinkId=196607) on the Microsoft Support website.</span></span>  
  
 <span data-ttu-id="015f2-110">Ten temat zawiera następujące sekcje:</span><span class="sxs-lookup"><span data-stu-id="015f2-110">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="015f2-111">Proces wdrażania</span><span class="sxs-lookup"><span data-stu-id="015f2-111">The deployment process</span></span>](#the_deployment_process)  
 [<span data-ttu-id="015f2-112">Wdrażanie programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="015f2-112">Deploying the .NET Framework</span></span>](#deploying_in_a_test_environment)  
 [<span data-ttu-id="015f2-113">Tworzenie kolekcji</span><span class="sxs-lookup"><span data-stu-id="015f2-113">Create a collection</span></span>](#creating_a_collection)  
 [<span data-ttu-id="015f2-114">Tworzenie pakietów i programów</span><span class="sxs-lookup"><span data-stu-id="015f2-114">Create a package and program</span></span>](#creating_a_package)  
 [<span data-ttu-id="015f2-115">Wybierz punkt dystrybucji</span><span class="sxs-lookup"><span data-stu-id="015f2-115">Select a distribution point</span></span>](#select_dist_point)  
 [<span data-ttu-id="015f2-116">Wdrażanie pakietu</span><span class="sxs-lookup"><span data-stu-id="015f2-116">Deploy the package</span></span>](#deploying_package)  
[<span data-ttu-id="015f2-117">Zasoby</span><span class="sxs-lookup"><span data-stu-id="015f2-117">Resources</span></span>](#resources)  
[<span data-ttu-id="015f2-118">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="015f2-118">Troubleshooting</span></span>](#troubleshooting)  
  
<a name="the_deployment_process"></a>   
## <a name="the-deployment-process"></a><span data-ttu-id="015f2-119">Proces wdrażania</span><span class="sxs-lookup"><span data-stu-id="015f2-119">The deployment process</span></span>  
 <span data-ttu-id="015f2-120">Gdy jest dostępna wymagana infrastruktura, należy użyć programu System Center 2012 Manager Configuration w celu wdrożenia pakietu redystrybucyjnego programu .NET Framework na komputerach w sieci.</span><span class="sxs-lookup"><span data-stu-id="015f2-120">When you have the supporting infrastructure in place, you use System Center 2012 Configuration Manager to deploy the .NET Framework redistributable package to computers on the network.</span></span> <span data-ttu-id="015f2-121">Tworzenie infrastruktury obejmuje utworzenie i zdefiniowanie pięciu podstawowych obszarów: kolekcji, pakietu i programu dla oprogramowania, punktów dystrybucji i wdrożeń.</span><span class="sxs-lookup"><span data-stu-id="015f2-121">Building the infrastructure involves creating and defining five primary areas: collections, a package and program for the software, distribution points, and deployments.</span></span>  
  
-   <span data-ttu-id="015f2-122">**Kolekcje** grup zasobów programu Configuration Manager, takich jak użytkownicy, grupy użytkowników lub komputerów, na których jest wdrożona programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="015f2-122">**Collections** are groups of Configuration Manager resources, such as users, user groups, or computers, to which the .NET Framework is deployed.</span></span> <span data-ttu-id="015f2-123">Aby uzyskać więcej informacji, zobacz [kolekcje w programie Configuration Manager](http://technet.microsoft.com/library/gg682169.aspx) w bibliotece dokumentacji programu Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="015f2-123">For more information, see [Collections in Configuration Manager](http://technet.microsoft.com/library/gg682169.aspx) in the Configuration Manager documentation library.</span></span>  
  
-   <span data-ttu-id="015f2-124">**Pakiety i programy** zazwyczaj reprezentują aplikacje do zainstalowania na komputerze klienckim, ale może także zawierać pojedyncze pliki, aktualizacji lub nawet poszczególnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="015f2-124">**Packages and programs** typically represent software applications to be installed on a client computer, but they might also contain individual files, updates, or even individual commands.</span></span> <span data-ttu-id="015f2-125">Aby uzyskać więcej informacji, zobacz [pakietów i programów w programie Configuration Manager](http://technet.microsoft.com/library/gg699369.aspx) w bibliotece dokumentacji programu Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="015f2-125">For more information, see [Packages and Programs in Configuration Manager](http://technet.microsoft.com/library/gg699369.aspx) in the Configuration Manager documentation library.</span></span>  
  
-   <span data-ttu-id="015f2-126">**Punkty dystrybucji** są role systemu, które przechowują pliki wymagane do działania oprogramowania na komputerach klienckich w lokacji programu Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="015f2-126">**Distribution points** are Configuration Manager site system roles that store files required for software to run on client computers.</span></span> <span data-ttu-id="015f2-127">Gdy klient programu Configuration Manager odbiera i przetwarza wdrożenie oprogramowania, kontaktuje się z punktem dystrybucji w celu pobrania zawartości skojarzonej z oprogramowaniem i rozpoczęcia procesu instalacji.</span><span class="sxs-lookup"><span data-stu-id="015f2-127">When the Configuration Manager client receives and processes a software deployment, it contacts a distribution point to download the content associated with the software and to start the installation process.</span></span> <span data-ttu-id="015f2-128">Aby uzyskać więcej informacji, zobacz [wprowadzenie do zarządzania zawartością w programie Configuration Manager](http://technet.microsoft.com/library/gg682083.aspx) w bibliotece dokumentacji programu Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="015f2-128">For more information, see [Introduction to content Management in Configuration Manager](http://technet.microsoft.com/library/gg682083.aspx) in the Configuration Manager documentation library.</span></span>  
  
-   <span data-ttu-id="015f2-129">**Wdrożenia** poinstruować odpowiednich członków kolekcji określone miejsce docelowe instalacji pakietu oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="015f2-129">**Deployments** instruct applicable members of the specified target collection to install the software package.</span></span> <span data-ttu-id="015f2-130">Aby uzyskać więcej informacji, zobacz [jak wdrażać aplikacje w programie Configuration Manager](http://technet.microsoft.com/library/gg682082.aspx) w bibliotece dokumentacji programu Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="015f2-130">For more information, see [How to Deploy Applications in Configuration Manager](http://technet.microsoft.com/library/gg682082.aspx) in the Configuration Manager documentation library.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="015f2-131">Procedury opisane w tym temacie zawierają typowe ustawienia służące do tworzenia i wdrażania pakietu oraz programu i mogą nie obejmować wszystkich możliwych ustawień.</span><span class="sxs-lookup"><span data-stu-id="015f2-131">The procedures in this topic contain typical settings for creating and deploying a package and program, and might not cover all possible settings.</span></span> <span data-ttu-id="015f2-132">Inne opcje wdrożenia programu Configuration Manager, zobacz [biblioteka dokumentacji programu Configuration Manager](http://technet.microsoft.com/library/gg682041.aspx).</span><span class="sxs-lookup"><span data-stu-id="015f2-132">For other Configuration Manager deployment options, see the [Configuration Manager Documentation Library](http://technet.microsoft.com/library/gg682041.aspx).</span></span>  
  
<a name="deploying_in_a_test_environment"></a>   
## <a name="deploying-the-net-framework"></a><span data-ttu-id="015f2-133">Wdrażanie programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="015f2-133">Deploying the .NET Framework</span></span>  
 <span data-ttu-id="015f2-134">System Center 2012 Configuration Manager można użyć do wdrożenia instalacji dyskretnej [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], których użytkownicy nie wchodzą w interakcje z procesu instalacji.</span><span class="sxs-lookup"><span data-stu-id="015f2-134">You can use System Center 2012 Configuration Manager to deploy a silent installation of the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], where the users do not interact with the installation process.</span></span> <span data-ttu-id="015f2-135">Wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="015f2-135">Follow these steps:</span></span>  
  
1.  <span data-ttu-id="015f2-136">[Utwórz kolekcję](#creating_a_collection).</span><span class="sxs-lookup"><span data-stu-id="015f2-136">[Create a collection](#creating_a_collection).</span></span>  
  
2.  <span data-ttu-id="015f2-137">[Tworzenie pakietów i programów dla programu .NET Framework redistributable](#creating_a_package).</span><span class="sxs-lookup"><span data-stu-id="015f2-137">[Create a package and program for the .NET Framework redistributable](#creating_a_package).</span></span>  
  
3.  <span data-ttu-id="015f2-138">[Wybierz punkt dystrybucji](#select_dist_point).</span><span class="sxs-lookup"><span data-stu-id="015f2-138">[Select a distribution point](#select_dist_point).</span></span>  
  
4.  <span data-ttu-id="015f2-139">[Wdrażanie pakietu](#deploying_package).</span><span class="sxs-lookup"><span data-stu-id="015f2-139">[Deploy the package](#deploying_package).</span></span>  
  
<a name="creating_a_collection"></a>   
### <a name="create-a-collection"></a><span data-ttu-id="015f2-140">Tworzenie kolekcji</span><span class="sxs-lookup"><span data-stu-id="015f2-140">Create a collection</span></span>  
 <span data-ttu-id="015f2-141">W tym kroku należy wybrać komputery, na których będzie wdrażany pakiet i program, i zgrupować je w kolekcji urządzeń.</span><span class="sxs-lookup"><span data-stu-id="015f2-141">In this step, you select the computers to which you will deploy the package and program, and group them into a device collection.</span></span> <span data-ttu-id="015f2-142">Aby utworzyć kolekcję w programie Configuration Manager, można użyć bezpośrednich reguł członkostwa (elementy członkowskie kolekcji są określane ręcznie) lub reguł zapytań (program Configuration Manager określa elementy członkowskie kolekcji na podstawie określonych kryteriów).</span><span class="sxs-lookup"><span data-stu-id="015f2-142">To create a collection in Configuration Manager, you can use direct membership rules (where you manually specify the collection members) or query rules (where Configuration Manager determines the collection members based on criteria you specify).</span></span> <span data-ttu-id="015f2-143">Aby uzyskać więcej informacji na temat reguł członkostwa, w tym zapytania i bezpośredniego reguły, zobacz [wprowadzenie do kolekcji w programie Configuration Manager](http://technet.microsoft.com/library/gg682177.aspx) w bibliotece dokumentacji programu Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="015f2-143">For more information about membership rules, including queries and direct rules, see [Introduction to Collections in Configuration Manager](http://technet.microsoft.com/library/gg682177.aspx) in the Configuration Manager Documentation Library.</span></span>  
  
 <span data-ttu-id="015f2-144">Aby utworzyć kolekcję:</span><span class="sxs-lookup"><span data-stu-id="015f2-144">To create a collection:</span></span>  
  
1.  <span data-ttu-id="015f2-145">W konsoli programu Configuration Manager wybierz **zasoby i zgodność**.</span><span class="sxs-lookup"><span data-stu-id="015f2-145">In the Configuration Manager console, choose **Assets and Compliance**.</span></span>  
  
2.  <span data-ttu-id="015f2-146">W **zasoby i zgodność** obszaru roboczego wybierz **kolekcje urządzeń**.</span><span class="sxs-lookup"><span data-stu-id="015f2-146">In the **Assets and Compliance** workspace, choose **Device Collections**.</span></span>  
  
3.  <span data-ttu-id="015f2-147">Na **Home** karcie **Utwórz** grupy, wybierz **Utwórz kolekcję urządzeń**.</span><span class="sxs-lookup"><span data-stu-id="015f2-147">On the **Home** tab in the **Create** group, choose **Create Device Collection**.</span></span>  
  
4.  <span data-ttu-id="015f2-148">Na **ogólne** strony **Kreatora tworzenia kolekcji urządzeń**, wprowadź nazwę kolekcji.</span><span class="sxs-lookup"><span data-stu-id="015f2-148">On the **General** page of the **Create Device Collection Wizard**, enter a name for the collection.</span></span>  
  
5.  <span data-ttu-id="015f2-149">Wybierz **Przeglądaj** do określenia kolekcji ograniczającej.</span><span class="sxs-lookup"><span data-stu-id="015f2-149">Choose **Browse** to specify a limiting collection.</span></span>  
  
6.  <span data-ttu-id="015f2-150">Na **reguł członkostwa** wybierz pozycję **Dodaj regułę**, a następnie wybierz pozycję **reguły bezpośredniej** otworzyć **bezpośredniego Kreatora tworzenia reguły członkostwa**.</span><span class="sxs-lookup"><span data-stu-id="015f2-150">On the **Membership Rules** page, choose **Add Rule**, and then choose **Direct Rule** to open the **Create Direct Membership Rule Wizard**.</span></span> <span data-ttu-id="015f2-151">Wybierz **dalej**.</span><span class="sxs-lookup"><span data-stu-id="015f2-151">Choose **Next**.</span></span>  
  
7.  <span data-ttu-id="015f2-152">Na **wyszukiwanie zasobów** strony w **klasy zasobów** wybierz **zasób systemowy**.</span><span class="sxs-lookup"><span data-stu-id="015f2-152">On the **Search for Resources** page, in the **Resource class** list, choose **System Resource**.</span></span> <span data-ttu-id="015f2-153">W **nazwa atrybutu** wybierz **nazwa**.</span><span class="sxs-lookup"><span data-stu-id="015f2-153">In the **Attribute name** list, choose **Name**.</span></span> <span data-ttu-id="015f2-154">W **wartość** wprowadź `%`, a następnie wybierz pozycję **dalej**.</span><span class="sxs-lookup"><span data-stu-id="015f2-154">In the **Value** field, enter `%`, and then choose **Next**.</span></span>  
  
8.  <span data-ttu-id="015f2-155">Na **zasobów wybierz** strony, zaznacz pole wyboru dla każdego komputera, który chcesz wdrożyć .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="015f2-155">On the **Select Resources** page, select the check box for each computer that you want to deploy the .NET Framework to.</span></span> <span data-ttu-id="015f2-156">Wybierz **dalej**, a następnie Zakończ pracę kreatora.</span><span class="sxs-lookup"><span data-stu-id="015f2-156">Choose **Next**, and then complete the wizard.</span></span>  
  
9. <span data-ttu-id="015f2-157">Na **reguł członkostwa** strony **Kreatora tworzenia kolekcji urządzeń**, wybierz **dalej**, a następnie Zakończ pracę kreatora.</span><span class="sxs-lookup"><span data-stu-id="015f2-157">On the **Membership Rules** page of the **Create Device Collection Wizard**, choose **Next**, and then complete the wizard.</span></span>  
  
 <span data-ttu-id="015f2-158">Aby uzyskać więcej informacji o kolekcjach, zobacz [kolekcje w programie Configuration Manager](http://technet.microsoft.com/library/bb693730.aspx) w bibliotece dokumentacji programu Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="015f2-158">For more information about collections, see [Collections in Configuration Manager](http://technet.microsoft.com/library/bb693730.aspx) in the Configuration Manager Documentation Library.</span></span>  
  
<a name="creating_a_package"></a>   
### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a><span data-ttu-id="015f2-159">Tworzenie pakietu i programu dla redystrybucyjnego pakietu programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="015f2-159">Create a package and program for the .NET Framework redistributable package</span></span>  
 <span data-ttu-id="015f2-160">Wykonanie poniższych kroków umożliwia ręczne utworzenie pakietu redystrybucyjnego programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="015f2-160">The following steps create a package for the .NET Framework redistributable manually.</span></span> <span data-ttu-id="015f2-161">Pakiet będzie zawierał określone parametry instalacji programu .NET Framework oraz lokalizację, z której pakiet będzie dystrybuowany na komputery docelowe.</span><span class="sxs-lookup"><span data-stu-id="015f2-161">The package contains the specified parameters for installing the .NET Framework and the location from where the package will be distributed to the target computers.</span></span>  
  
 <span data-ttu-id="015f2-162">Aby utworzyć pakiet:</span><span class="sxs-lookup"><span data-stu-id="015f2-162">To create a package:</span></span>  
  
1.  <span data-ttu-id="015f2-163">W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania**...</span><span class="sxs-lookup"><span data-stu-id="015f2-163">In the Configuration Manager console, choose **Software Library**..</span></span>  
  
2.  <span data-ttu-id="015f2-164">W **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **Zarządzanie aplikacjami**, a następnie wybierz pozycję **pakiety**.</span><span class="sxs-lookup"><span data-stu-id="015f2-164">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>  
  
3.  <span data-ttu-id="015f2-165">Na **Home** karcie **Utwórz** grupy, wybierz **tworzenia pakietu**.</span><span class="sxs-lookup"><span data-stu-id="015f2-165">On the **Home** tab, in the **Create** group, choose **Create Package**.</span></span>  
  
4.  <span data-ttu-id="015f2-166">Na **pakietu** strony **Kreatora tworzenia pakietu i programu**, wprowadź następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="015f2-166">On the **Package** page of the **Create Package and Program Wizard**, enter the following information:</span></span>  
  
    -   <span data-ttu-id="015f2-167">Nazwa: `.NET Framework 4.5`</span><span class="sxs-lookup"><span data-stu-id="015f2-167">Name: `.NET Framework 4.5`</span></span>  
  
    -   <span data-ttu-id="015f2-168">Producent: `Microsoft`</span><span class="sxs-lookup"><span data-stu-id="015f2-168">Manufacturer: `Microsoft`</span></span>  
  
    -   <span data-ttu-id="015f2-169">Język.</span><span class="sxs-lookup"><span data-stu-id="015f2-169">Language.</span></span> `English (US)`  
  
5.  <span data-ttu-id="015f2-170">Wybierz **ten pakiet zawiera pliki źródłowe**, a następnie wybierz pozycję **Przeglądaj** do wybierz lokalnego lub sieciową folderu zawierającego pliki instalacyjne programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="015f2-170">Choose **This package contains source files**, and then choose **Browse** to select the local or network folder that contains the .NET Framework installation files.</span></span> <span data-ttu-id="015f2-171">Po wybraniu folderu, wybierz **OK**, a następnie wybierz pozycję **dalej**.</span><span class="sxs-lookup"><span data-stu-id="015f2-171">When you have selected the folder, choose **OK**, and then choose **Next**.</span></span>  
  
6.  <span data-ttu-id="015f2-172">Na **typu programu** strony kreatora wybierz **Program standardowy**, a następnie wybierz pozycję **dalej**.</span><span class="sxs-lookup"><span data-stu-id="015f2-172">On the **Program Type** page of the wizard, choose **Standard Program**, and then choose **Next**.</span></span>  
  
7.  <span data-ttu-id="015f2-173">Na **Program** strony **Kreatora tworzenia pakietu i programu**, wprowadź następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="015f2-173">On the **Program** page of the **Create Package and Program Wizard**, enter the following information:</span></span>  
  
    1.  <span data-ttu-id="015f2-174">**Nazwa:** `.NET Framework 4.5`</span><span class="sxs-lookup"><span data-stu-id="015f2-174">**Name:** `.NET Framework 4.5`</span></span>  
  
    2.  <span data-ttu-id="015f2-175">**Wiersz polecenia:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (Opcje wiersza polecenia są opisane w tabeli po wykonaniu tych kroków)</span><span class="sxs-lookup"><span data-stu-id="015f2-175">**Command line:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (command-line options are described in the table after these steps)</span></span>  
  
    3.  <span data-ttu-id="015f2-176">**Instalacja:** wybierz **ukryte**.</span><span class="sxs-lookup"><span data-stu-id="015f2-176">**Run:** Choose **Hidden**.</span></span>  
  
    4.  <span data-ttu-id="015f2-177">**Program może zostać uruchomiony:** wybierz opcję określającą, czy program można uruchomić niezależnie od tego, czy użytkownik jest zalogowany.</span><span class="sxs-lookup"><span data-stu-id="015f2-177">**Program can run:** Choose the option that specifies that the program can run regardless of whether a user is logged on.</span></span>  
  
8.  <span data-ttu-id="015f2-178">Na **wymagania** wybierz pozycję **dalej** można zaakceptować wartości domyślne, a następnie Zakończ pracę kreatora.</span><span class="sxs-lookup"><span data-stu-id="015f2-178">On the **Requirements** page, choose **Next** to accept the default values, and then complete the wizard.</span></span>  
  
 <span data-ttu-id="015f2-179">W poniższej tabeli opisano opcje wiersza polecenia określone w kroku 7.</span><span class="sxs-lookup"><span data-stu-id="015f2-179">The following table describes the command-line options specified in step 7.</span></span>  
  
|<span data-ttu-id="015f2-180">Opcja</span><span class="sxs-lookup"><span data-stu-id="015f2-180">Option</span></span>|<span data-ttu-id="015f2-181">Opis</span><span class="sxs-lookup"><span data-stu-id="015f2-181">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="015f2-182">**/q**</span><span class="sxs-lookup"><span data-stu-id="015f2-182">**/q**</span></span>|<span data-ttu-id="015f2-183">Ustawia tryb cichy.</span><span class="sxs-lookup"><span data-stu-id="015f2-183">Sets quiet mode.</span></span> <span data-ttu-id="015f2-184">Nie jest wymagane wprowadzanie danych przez użytkownika i nie są wyświetlane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="015f2-184">No user input is required, and no output is shown.</span></span>|  
|<span data-ttu-id="015f2-185">**/norestart**</span><span class="sxs-lookup"><span data-stu-id="015f2-185">**/norestart**</span></span>|<span data-ttu-id="015f2-186">Uniemożliwia Instalatorowi automatyczne wykonywanie ponownego rozruchu.</span><span class="sxs-lookup"><span data-stu-id="015f2-186">Prevents the Setup program from rebooting automatically.</span></span> <span data-ttu-id="015f2-187">Użycie tej opcji spowoduje, że program Configuration Manager będzie musiał obsługiwać ponowne uruchamianie komputera.</span><span class="sxs-lookup"><span data-stu-id="015f2-187">If you use this option, Configuration Manager must handle the computer restart.</span></span>|  
|<span data-ttu-id="015f2-188">**/chainingpackage** *PackageName*</span><span class="sxs-lookup"><span data-stu-id="015f2-188">**/chainingpackage** *PackageName*</span></span>|<span data-ttu-id="015f2-189">Określa nazwę pakietu, który tworzy łańcuch.</span><span class="sxs-lookup"><span data-stu-id="015f2-189">Specifies the name of the package that is doing the chaining.</span></span> <span data-ttu-id="015f2-190">Te informacje były zgłaszane z innych informacji o sesji instalacji dla tych, którzy zalogowali się [Program poprawy jakości obsługi programu Microsoft klienta (CEIP)](http://go.microsoft.com/fwlink/p/?LinkId=248244).</span><span class="sxs-lookup"><span data-stu-id="015f2-190">This information is reported with other installation session information for those who have signed up for the [Microsoft Customer Experience Improvement Program (CEIP)](http://go.microsoft.com/fwlink/p/?LinkId=248244).</span></span> <span data-ttu-id="015f2-191">Jeśli nazwa pakietu zawiera spacje, użyj podwójnych cudzysłowów prostych jako ograniczników; na przykład: **/chainingpackage "Łańcucha produktu"**.</span><span class="sxs-lookup"><span data-stu-id="015f2-191">If the package name includes spaces, use double quotation marks as delimiters; for example: **/chainingpackage "Chaining Product"**.</span></span>|  
  
 <span data-ttu-id="015f2-192">Wykonanie tych kroków spowoduje utworzenie pakietu o nazwie .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="015f2-192">These steps create a package named .NET Framework 4.5.</span></span> <span data-ttu-id="015f2-193">Program wdraża instalację dyskretną programu .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="015f2-193">The program deploys a silent installation of the .NET Framework 4.5.</span></span> <span data-ttu-id="015f2-194">W przypadku instalacji dyskretnej użytkownicy nie interakcji z procesu instalacji i CBC aplikacja ma kod powrotny przechwytywania i ponowne uruchomienie; zobacz [uzyskiwanie informacji o postępie z pakietu instalacyjnego](http://go.microsoft.com/fwlink/?LinkId=179606).</span><span class="sxs-lookup"><span data-stu-id="015f2-194">In a silent installation, users do not interact with the installation process, and the chaining application has to capture the return code and handle rebooting; see [Getting Progress Information from an Installation Package](http://go.microsoft.com/fwlink/?LinkId=179606).</span></span>  
 
<a name="select_dist_point"></a>   
### <a name="select-a-distribution-point"></a><span data-ttu-id="015f2-195">Wybieranie punktu dystrybucji</span><span class="sxs-lookup"><span data-stu-id="015f2-195">Select a distribution point</span></span>  
 <span data-ttu-id="015f2-196">Aby dystrybuować pakiet i program na komputery klienckie z serwera, należy najpierw wyznaczyć system lokacji jako punkt dystrybucji, a następnie dystrybuować pakiet do punktu dystrybucji.</span><span class="sxs-lookup"><span data-stu-id="015f2-196">To distribute the package and program to client computers from a server, you must first designate a site system as a distribution point and then distribute the package to the distribution point.</span></span>  
  
 <span data-ttu-id="015f2-197">Wykonując poniższe kroki, można wybrać punkt dystrybucji dla pakietu programu .NET Framework 4.5 utworzonego w poprzedniej sekcji:</span><span class="sxs-lookup"><span data-stu-id="015f2-197">Use the following steps to select a distribution point for the .NET Framework 4.5 package you created in the previous section:</span></span>  
  
1.  <span data-ttu-id="015f2-198">W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania**.</span><span class="sxs-lookup"><span data-stu-id="015f2-198">In the Configuration Manager console, choose **Software Library**.</span></span>  
  
2.  <span data-ttu-id="015f2-199">W **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **Zarządzanie aplikacjami**, a następnie wybierz pozycję **pakiety**.</span><span class="sxs-lookup"><span data-stu-id="015f2-199">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>  
  
3.  <span data-ttu-id="015f2-200">Wybierz pakiet z listy pakietów **.NET Framework 4.5** utworzoną w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="015f2-200">From the list of packages, select the package **.NET Framework 4.5** that you created in the previous section.</span></span>  
  
4.  <span data-ttu-id="015f2-201">Na **Home** karcie **wdrożenia** grupy, wybierz **Dystrybuuj zawartość**.</span><span class="sxs-lookup"><span data-stu-id="015f2-201">On the **Home** tab, in the **Deployment** group, choose **Distribute Content**.</span></span>  
  
5.  <span data-ttu-id="015f2-202">Na **ogólne** karcie **kreatora dystrybucji zawartości**, wybierz **dalej**.</span><span class="sxs-lookup"><span data-stu-id="015f2-202">On the **General** tab of the **Distribute Content Wizard**, choose **Next**.</span></span>  
  
6.  <span data-ttu-id="015f2-203">Na **miejsce docelowe zawartości** strony kreatora wybierz **Dodaj**, a następnie wybierz pozycję **punktu dystrybucji**.</span><span class="sxs-lookup"><span data-stu-id="015f2-203">On the **Content Destination** page of the wizard, choose **Add**, and then choose **Distribution Point**.</span></span>  
  
7.  <span data-ttu-id="015f2-204">W **punktów dystrybucji Dodaj** oknie dialogowym Wybierz punkty dystrybucji, który hosta pakiet i program, a następnie wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="015f2-204">In the **Add Distribution Points** dialog box, select the distribution point(s) that will host the package and program, and then choose **OK**.</span></span>  
  
8.  <span data-ttu-id="015f2-205">Ukończ pracę kreatora.</span><span class="sxs-lookup"><span data-stu-id="015f2-205">Complete the wizard.</span></span>  
  
 <span data-ttu-id="015f2-206">Packagenow zawiera wszystkie informacje, które należy wdrożyć w trybie dyskretnym .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="015f2-206">The packagenow contains all the information you need to silently deploy the .NET Framework 4.5.</span></span> <span data-ttu-id="015f2-207">Przed przystąpieniem do wdrażania pakietów i programów, sprawdź, czy został zainstalowany w punkcie dystrybucji; zobacz sekcję "Monitor zawartość" [operacje i Obsługa zarządzania zawartością w programie Configuration Manager](http://technet.microsoft.com/library/gg712694.aspx#BKMK_MonitorContent) w bibliotece dokumentacji programu Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="015f2-207">Before you deploy the package and program, verify that it was installed on the distribution point; see the "Monitor Content" section of [Operations and Maintenance for Content Management in Configuration Manager](http://technet.microsoft.com/library/gg712694.aspx#BKMK_MonitorContent) in the Configuration Manager Documentation Library.</span></span>  
  
<a name="deploying_package"></a>   
### <a name="deploy-the-package"></a><span data-ttu-id="015f2-208">Wdrażanie pakietu</span><span class="sxs-lookup"><span data-stu-id="015f2-208">Deploy the package</span></span>  
 <span data-ttu-id="015f2-209">Aby wdrożyć pakiet i program .NET Framework 4.5:</span><span class="sxs-lookup"><span data-stu-id="015f2-209">To deploy the .NET Framework 4.5 package and program:</span></span>  
  
1.  <span data-ttu-id="015f2-210">W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania**.</span><span class="sxs-lookup"><span data-stu-id="015f2-210">In the Configuration Manager console, choose **Software Library**.</span></span>  
  
2.  <span data-ttu-id="015f2-211">W **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **Zarządzanie aplikacjami**, a następnie wybierz pozycję **pakiety**.</span><span class="sxs-lookup"><span data-stu-id="015f2-211">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>  
  
3.  <span data-ttu-id="015f2-212">Z listy pakietów, wybierz pakiet utworzony o nazwie **.NET Framework 4.5**.</span><span class="sxs-lookup"><span data-stu-id="015f2-212">From the list of packages, select the package you created named **.NET Framework 4.5**.</span></span>  
  
4.  <span data-ttu-id="015f2-213">Na **Home** karcie **wdrożenia** grupy, wybierz **Wdróż**.</span><span class="sxs-lookup"><span data-stu-id="015f2-213">On the **Home** tab, in the **Deployment** group, choose **Deploy**.</span></span>  
  
5.  <span data-ttu-id="015f2-214">Na **ogólne** strony **Kreatora wdrażania oprogramowania**, wybierz **Przeglądaj**, a następnie wybierz kolekcję, do której został utworzony wcześniej.</span><span class="sxs-lookup"><span data-stu-id="015f2-214">On the **General** page of the **Deploy Software Wizard**, choose **Browse**, and then select the collection that you created earlier.</span></span> <span data-ttu-id="015f2-215">Wybierz **dalej**.</span><span class="sxs-lookup"><span data-stu-id="015f2-215">Choose **Next**.</span></span>  
  
6.  <span data-ttu-id="015f2-216">Na **zawartości** strony kreatora, sprawdź, czy jest wyświetlany punkt, z którego ma być dystrybucji oprogramowania, a następnie wybierz **dalej**.</span><span class="sxs-lookup"><span data-stu-id="015f2-216">On the **Content** page of the wizard, verify that the point from which you want to distribute the software is displayed, and then choose **Next**.</span></span>  
  
7.  <span data-ttu-id="015f2-217">Na **ustawienia wdrażania** strony kreatora upewnij się, że **akcji** ustawiono **zainstalować**, i **celu** ma ustawioną wartość **Wymagane**.</span><span class="sxs-lookup"><span data-stu-id="015f2-217">On the **Deployment Settings** page of the wizard, confirm that **Action** is set to **Install**, and **Purpose** is set to **Required**.</span></span> <span data-ttu-id="015f2-218">Te wartości ustawień gwarantują, że pakiet oprogramowania będzie obowiązkowo instalowany na komputerach docelowych.</span><span class="sxs-lookup"><span data-stu-id="015f2-218">This ensures that the software package will be a mandatory installation on the targeted computers.</span></span> <span data-ttu-id="015f2-219">Wybierz **dalej**.</span><span class="sxs-lookup"><span data-stu-id="015f2-219">Choose **Next**.</span></span>  
  
8.  <span data-ttu-id="015f2-220">Na **Planowanie** strony kreatora, określić, kiedy .NET Framework do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="015f2-220">On the **Scheduling** page of the wizard, specify when you want the .NET Framework to be installed.</span></span> <span data-ttu-id="015f2-221">Możesz wybrać **nowy** przypisywania czas instalacji, lub poinstruować oprogramowania do zainstalowania podczas logowania użytkownika na lub wyłączyć lub tak szybko, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="015f2-221">You can choose **New** to assign an installation time, or instruct the software to install when the user logs on or off, or as soon as possible.</span></span> <span data-ttu-id="015f2-222">Wybierz **dalej**.</span><span class="sxs-lookup"><span data-stu-id="015f2-222">Choose **Next**.</span></span>  
  
9. <span data-ttu-id="015f2-223">Na **środowisko użytkownika** kreatora Użyj domyślnej wartości i wybierz **dalej**.</span><span class="sxs-lookup"><span data-stu-id="015f2-223">On the **User Experience** page of the wizard, use the default values and choose **Next**.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="015f2-224">W środowisku produkcyjnym mogą obowiązywać zasady wymagające wybrania innych ustawień harmonogramu wdrażania.</span><span class="sxs-lookup"><span data-stu-id="015f2-224">Your production environment might have policies that require different selections for the deployment schedule.</span></span> <span data-ttu-id="015f2-225">Aby uzyskać informacje o tych opcjach, zobacz [anonsu nazwa właściwości: kartę Harmonogram](http://technet.microsoft.com/library/bb694016.aspx) w bibliotece TechNet.</span><span class="sxs-lookup"><span data-stu-id="015f2-225">For information about these options, see [Advertisement Name Properties: Schedule Tab](http://technet.microsoft.com/library/bb694016.aspx) in the TechNet Library.</span></span>  
  
10. <span data-ttu-id="015f2-226">Na **punktów dystrybucji** kreatora Użyj domyślnej wartości i wybierz **dalej**.</span><span class="sxs-lookup"><span data-stu-id="015f2-226">On the **Distribution Points** page of the wizard, use the default values and choose **Next**.</span></span>  
  
11. <span data-ttu-id="015f2-227">Ukończ pracę kreatora.</span><span class="sxs-lookup"><span data-stu-id="015f2-227">Complete the wizard.</span></span> <span data-ttu-id="015f2-228">Możesz monitorować postęp wdrażania w **wdrożeń** węzła **monitorowanie** obszaru roboczego.</span><span class="sxs-lookup"><span data-stu-id="015f2-228">You can monitor the progress of the deployment in the **Deployments** node of the **Monitoring** workspace.</span></span>  
  
 <span data-ttu-id="015f2-229">Teraz pakiet zostanie wdrożony w kolekcji docelowej i rozpocznie się dyskretna instalacja programu .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="015f2-229">The package will now be deployed to the targeted collection and the silent installation of .NET Framework 4.5 will begin.</span></span> <span data-ttu-id="015f2-230">Aby uzyskać informacje na temat kody błędów instalacji programu .NET Framework 4.5, zobacz [kody powrotne](#return_codes) później w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="015f2-230">For information about .NET Framework 4.5 installation error codes, see the [Return Codes](#return_codes) section later in this topic.</span></span>  
  
<a name="resources"></a>   
## <a name="resources"></a><span data-ttu-id="015f2-231">Zasoby</span><span class="sxs-lookup"><span data-stu-id="015f2-231">Resources</span></span>  
 <span data-ttu-id="015f2-232">Aby uzyskać więcej informacji dotyczących infrastruktury do testowania wdrożenia [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] do dystrybucji pakietu, zobacz następujące zasoby.</span><span class="sxs-lookup"><span data-stu-id="015f2-232">For more information about the infrastructure for testing the deployment of the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable package, see the following resources.</span></span>  
  
 <span data-ttu-id="015f2-233">**Usługi Active Directory, DNS, DHCP:**</span><span class="sxs-lookup"><span data-stu-id="015f2-233">**Active Directory, DNS, DHCP:**</span></span>  
  
-   [<span data-ttu-id="015f2-234">Usługi domenowe Active Directory systemu Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="015f2-234">Active Directory Domain Services for Windows Server 2008</span></span>](http://technet.microsoft.com/library/dd378891.aspx)  
  
-   [<span data-ttu-id="015f2-235">DNS Server</span><span class="sxs-lookup"><span data-stu-id="015f2-235">DNS Server</span></span>](http://technet.microsoft.com/library/cc732997.aspx)  
  
-   [<span data-ttu-id="015f2-236">Serwer DHCP</span><span class="sxs-lookup"><span data-stu-id="015f2-236">DHCP Server</span></span>](http://technet.microsoft.com/library/cc896553.aspx)  
  
 <span data-ttu-id="015f2-237">**SQL Server 2008:**</span><span class="sxs-lookup"><span data-stu-id="015f2-237">**SQL Server 2008:**</span></span>  
  
-   [<span data-ttu-id="015f2-238">Instalowanie programu SQL Server 2008 (SQL Server wideo)</span><span class="sxs-lookup"><span data-stu-id="015f2-238">Installing SQL Server 2008 (SQL Server Video)</span></span>](http://technet.microsoft.com/library/dd299415.aspx)  
  
-   [<span data-ttu-id="015f2-239">Omówienie usług SQL Server 2008 zabezpieczeń dla administratorów bazy danych</span><span class="sxs-lookup"><span data-stu-id="015f2-239">SQL Server 2008 Security Overview for Database Administrators</span></span>](http://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)  
  
 <span data-ttu-id="015f2-240">**System Center 2012 Configuration Manager, (punkt zarządzania, punkt dystrybucji):**</span><span class="sxs-lookup"><span data-stu-id="015f2-240">**System Center 2012 Configuration Manager (Management Point, Distribution Point):**</span></span>  
  
-   [<span data-ttu-id="015f2-241">Administrowanie witryną dla programu System Center 2012 Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="015f2-241">Site Administration for System Center 2012 Configuration Manager</span></span>](http://technet.microsoft.com/library/gg681983.aspx)  
  
-   [<span data-ttu-id="015f2-242">Menedżera konfiguracji pojedynczej lokacji planowania i wdrażania</span><span class="sxs-lookup"><span data-stu-id="015f2-242">Configuration Manager Single Site Planning and Deployment</span></span>](http://technet.microsoft.com/library/bb680961.aspx)  
  
 <span data-ttu-id="015f2-243">**Klient programu System Center 2012 Configuration Manager dla komputerów z systemem Windows:**</span><span class="sxs-lookup"><span data-stu-id="015f2-243">**System Center 2012 Configuration Manager client for Windows computers:**</span></span>  
  
-   [<span data-ttu-id="015f2-244">Wdrażanie klientów programu System Center 2012 Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="015f2-244">Deploying Clients for System Center 2012 Configuration Manager</span></span>](http://technet.microsoft.com/library/gg699391.aspx)  
  
<a name="troubleshooting"></a>   
## <a name="troubleshooting"></a><span data-ttu-id="015f2-245">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="015f2-245">Troubleshooting</span></span>  
  
### <a name="log-file-locations"></a><span data-ttu-id="015f2-246">Lokalizacje plików dziennika</span><span class="sxs-lookup"><span data-stu-id="015f2-246">Log file locations</span></span>  
 <span data-ttu-id="015f2-247">Następujące pliki dziennika są generowane podczas [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalatora:</span><span class="sxs-lookup"><span data-stu-id="015f2-247">The following log files are generated during [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup:</span></span>  
  
 <span data-ttu-id="015f2-248">%Temp%\Microsoft .NET framework 4.5*.txt %temp%\Microsoft .NET Framework 4.5*.html</span><span class="sxs-lookup"><span data-stu-id="015f2-248">%temp%\Microsoft .NET Framework 4.5*.txt %temp%\Microsoft .NET Framework 4.5*.html</span></span>  
  
 <span data-ttu-id="015f2-249">Można użyć [narzędzie do zbierania dzienników](http://www.microsoft.com/download/details.aspx?id=12493) służąca do gromadzenia [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] plików dziennika i utworzyć plik skompresowany plik cabinet (cab), która ogranicza rozmiar plików.</span><span class="sxs-lookup"><span data-stu-id="015f2-249">You can use the [log collection tool](http://www.microsoft.com/download/details.aspx?id=12493) to collect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] log files and to create a compressed cabinet (.cab) file that reduces the size of the files.</span></span>  
  
<a name="return_codes"></a>   
### <a name="return-codes"></a><span data-ttu-id="015f2-250">Kody powrotne</span><span class="sxs-lookup"><span data-stu-id="015f2-250">Return codes</span></span>  
 <span data-ttu-id="015f2-251">W poniższej tabeli wymieniono zwraca najbardziej typowe kody z [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] instalacji pakietu redystrybucyjnego programu.</span><span class="sxs-lookup"><span data-stu-id="015f2-251">The following table lists the most common return codes from the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable installation program.</span></span> <span data-ttu-id="015f2-252">Kody powrotne są takie same dla wszystkich wersji instalatora.</span><span class="sxs-lookup"><span data-stu-id="015f2-252">The return codes are the same for all versions of the installer.</span></span>  
  
 <span data-ttu-id="015f2-253">Dla łącza, aby uzyskać szczegółowe informacje, zobacz następną sekcję, [Pobierz kody błędów](#additional_error_codes).</span><span class="sxs-lookup"><span data-stu-id="015f2-253">For links to detailed information, see the next section, [Download error codes](#additional_error_codes).</span></span>  
  
|<span data-ttu-id="015f2-254">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="015f2-254">Return code</span></span>|<span data-ttu-id="015f2-255">Opis</span><span class="sxs-lookup"><span data-stu-id="015f2-255">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="015f2-256">0</span><span class="sxs-lookup"><span data-stu-id="015f2-256">0</span></span>|<span data-ttu-id="015f2-257">Instalacja została zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="015f2-257">Installation completed successfully.</span></span>|  
|<span data-ttu-id="015f2-258">1602</span><span class="sxs-lookup"><span data-stu-id="015f2-258">1602</span></span>|<span data-ttu-id="015f2-259">Użytkownik anulował instalację.</span><span class="sxs-lookup"><span data-stu-id="015f2-259">The user canceled installation.</span></span>|  
|<span data-ttu-id="015f2-260">1603</span><span class="sxs-lookup"><span data-stu-id="015f2-260">1603</span></span>|<span data-ttu-id="015f2-261">Podczas instalacji wystąpił błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="015f2-261">A fatal error occurred during installation.</span></span>|  
|<span data-ttu-id="015f2-262">1641</span><span class="sxs-lookup"><span data-stu-id="015f2-262">1641</span></span>|<span data-ttu-id="015f2-263">Do ukończenia instalacji wymagane jest ponowne uruchomienie komputera.</span><span class="sxs-lookup"><span data-stu-id="015f2-263">A restart is required to complete the installation.</span></span> <span data-ttu-id="015f2-264">Ten komunikat oznacza sukces.</span><span class="sxs-lookup"><span data-stu-id="015f2-264">This message indicates success.</span></span>|  
|<span data-ttu-id="015f2-265">3010</span><span class="sxs-lookup"><span data-stu-id="015f2-265">3010</span></span>|<span data-ttu-id="015f2-266">Do ukończenia instalacji wymagane jest ponowne uruchomienie komputera.</span><span class="sxs-lookup"><span data-stu-id="015f2-266">A restart is required to complete the installation.</span></span> <span data-ttu-id="015f2-267">Ten komunikat oznacza sukces.</span><span class="sxs-lookup"><span data-stu-id="015f2-267">This message indicates success.</span></span>|  
|<span data-ttu-id="015f2-268">5100</span><span class="sxs-lookup"><span data-stu-id="015f2-268">5100</span></span>|<span data-ttu-id="015f2-269">Komputer użytkownika nie spełnia wymagań systemowych.</span><span class="sxs-lookup"><span data-stu-id="015f2-269">The user's computer does not meet system requirements.</span></span>|  
  
<a name="additional_error_codes"></a>   
### <a name="download-error-codes"></a><span data-ttu-id="015f2-270">Kody błędów pobierania</span><span class="sxs-lookup"><span data-stu-id="015f2-270">Download error codes</span></span>  
  
-   [<span data-ttu-id="015f2-271">Kody błędów Background Intelligent Transfer Service (BITS)</span><span class="sxs-lookup"><span data-stu-id="015f2-271">Background Intelligent Transfer Service (BITS) error codes</span></span>](http://msdn.microsoft.com/library/aa362823.aspx)  
  
-   [<span data-ttu-id="015f2-272">Kody błędów moniker adresu URL</span><span class="sxs-lookup"><span data-stu-id="015f2-272">URL moniker error codes</span></span>](http://msdn.microsoft.com/library/ms775145.aspx)  
  
-   [<span data-ttu-id="015f2-273">Kody błędów WinHttp</span><span class="sxs-lookup"><span data-stu-id="015f2-273">WinHttp error codes</span></span>](http://msdn.microsoft.com/library/aa383770.aspx)  
  
 <span data-ttu-id="015f2-274">Inne kody błędów:</span><span class="sxs-lookup"><span data-stu-id="015f2-274">Other error codes:</span></span>  
  
-   [<span data-ttu-id="015f2-275">Kody błędów Instalatora Windows</span><span class="sxs-lookup"><span data-stu-id="015f2-275">Windows Installer error codes</span></span>](http://msdn.microsoft.com/library/aa368542.aspx)  
  
-   [<span data-ttu-id="015f2-276">Kody wyników programu Windows Update Agent</span><span class="sxs-lookup"><span data-stu-id="015f2-276">Windows Update Agent result codes</span></span>](http://technet.microsoft.com/library/cc720442.aspx)  
  
## <a name="see-also"></a><span data-ttu-id="015f2-277">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="015f2-277">See Also</span></span>  
 [<span data-ttu-id="015f2-278">Przewodnik wdrażania dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="015f2-278">Deployment Guide for Developers</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 [<span data-ttu-id="015f2-279">Wymagania systemowe</span><span class="sxs-lookup"><span data-stu-id="015f2-279">System Requirements</span></span>](../../../docs/framework/get-started/system-requirements.md)
