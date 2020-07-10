---
title: Migrowanie aplikacji sieci Web ASP.NET na maszynę wirtualną platformy Azure
description: Dowiedz się, jak migrować aplikację sieci Web ASP.NET z lokalnego na maszynę wirtualną platformy Azure.
ms.topic: how-to
ms.date: 06/20/2020
ms.openlocfilehash: 5ef340d020b72bebe46fe598fe68e7d02d0c0363
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174247"
---
# <a name="migrate-an-aspnet-web-application-to-an-azure-virtual-machine"></a><span data-ttu-id="aea6a-103">Migrowanie aplikacji sieci Web ASP.NET na maszynę wirtualną platformy Azure</span><span class="sxs-lookup"><span data-stu-id="aea6a-103">Migrate an ASP.NET Web application to an Azure Virtual Machine</span></span>

<span data-ttu-id="aea6a-104">Ten dokument zawiera omówienie sposobu migrowania aplikacji sieci Web ASP.NET z lokalizacji lokalnej na maszynę wirtualną platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="aea6a-104">This document provides an overview of how to migrate an ASP.NET web application from on-premises to an Azure Virtual Machine.</span></span>

## <a name="quickstart"></a><span data-ttu-id="aea6a-105">Szybki start</span><span class="sxs-lookup"><span data-stu-id="aea6a-105">Quickstart</span></span>

<span data-ttu-id="aea6a-106">Dowiedz się, jak utworzyć maszynę wirtualną i opublikować w niej aplikację: [Publikowanie na maszynie wirtualnej platformy Azure](https://tutorials.visualstudio.com/aspnet-vm/intro)</span><span class="sxs-lookup"><span data-stu-id="aea6a-106">Learn how to create a virtual machine and publish your app to it: [Publish to an Azure VM](https://tutorials.visualstudio.com/aspnet-vm/intro)</span></span>

## <a name="get-started"></a><span data-ttu-id="aea6a-107">Rozpocznij</span><span class="sxs-lookup"><span data-stu-id="aea6a-107">Get Started</span></span>

<span data-ttu-id="aea6a-108">Te samouczki demonstrują procedurę tworzenia (lub migrowania) maszyny wirtualnej, publikowania w niej aplikacji sieci Web oraz innych zadań, które mogą być wymagane do obsługi aplikacji na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="aea6a-108">These tutorials demonstrate the steps to create (or migrate) a virtual machine, publish your web application to it, and other tasks that may be required to support your application in Azure.</span></span>

- <span data-ttu-id="aea6a-109">Utwórz maszynę wirtualną dla swojej aplikacji ASP.NET na platformie Azure przy użyciu jednej z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="aea6a-109">Create a virtual machine for your ASP.NET application in Azure using one of the following options:</span></span>
  - [<span data-ttu-id="aea6a-110">Utwórz nową maszynę wirtualną dla aplikacji ASP.NET</span><span class="sxs-lookup"><span data-stu-id="aea6a-110">Create a new virtual machine for ASP.NET Applications</span></span>](https://go.microsoft.com/fwlink/?linkid=863237)
  - [<span data-ttu-id="aea6a-111">Migrowanie istniejącej lokalnej maszyny wirtualnej VMWare</span><span class="sxs-lookup"><span data-stu-id="aea6a-111">Migrate an existing on-premises VMWare virtual machine</span></span>](/azure/migrate/tutorial-migrate-vmware)
  - [<span data-ttu-id="aea6a-112">Migrowanie istniejącej lokalnej maszyny wirtualnej funkcji Hyper-V</span><span class="sxs-lookup"><span data-stu-id="aea6a-112">Migrate an existing on-premises Hyper-V virtual machine</span></span>](/azure/migrate/tutorial-migrate-hyper-v)
- [<span data-ttu-id="aea6a-113">Publikowanie aplikacji przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="aea6a-113">Publish your app using Visual Studio</span></span>](https://go.microsoft.com/fwlink/?linkid=863240)
- [<span data-ttu-id="aea6a-114">Tworzenie bezpiecznej sieci wirtualnej dla maszyn wirtualnych</span><span class="sxs-lookup"><span data-stu-id="aea6a-114">Create a secure virtual network for your VMs</span></span>](/azure/virtual-network/virtual-network-get-started-vnet-subnet)
- [<span data-ttu-id="aea6a-115">Tworzenie potoku ciągłej integracji/ciągłego wdrażania dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="aea6a-115">Create a CI/CD pipeline for your application</span></span>](/vsts/build-release/apps/cd/deploy-webdeploy-iis-deploygroups)
- [<span data-ttu-id="aea6a-116">Przejdź do zestawu skalowania maszyn wirtualnych w celu zapewnienia wysokiej dostępności i skalowalności</span><span class="sxs-lookup"><span data-stu-id="aea6a-116">Move to a VM scale set for high availability and scalability</span></span>](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)

## <a name="considerations"></a><span data-ttu-id="aea6a-117">Kwestie do rozważenia</span><span class="sxs-lookup"><span data-stu-id="aea6a-117">Considerations</span></span>

### <a name="benefits"></a><span data-ttu-id="aea6a-118">Korzyści</span><span class="sxs-lookup"><span data-stu-id="aea6a-118">Benefits</span></span>

<span data-ttu-id="aea6a-119">Usługa Virtual Machines oferuje najprostszą ścieżkę do migracji aplikacji z lokalizacji lokalnej do chmury.</span><span class="sxs-lookup"><span data-stu-id="aea6a-119">Virtual machines offer the easiest path to migrate an application from on-premises to the cloud.</span></span> <span data-ttu-id="aea6a-120">Umożliwiają one replikację tego samego środowiska, w którym aplikacja jest stosowana lokalnie, a jednocześnie eliminuje konieczność utrzymania własnych centrów danych.</span><span class="sxs-lookup"><span data-stu-id="aea6a-120">They enable you to replicate the same environment your application uses on-premises, while removing the need to maintain your own data centers.</span></span> <span data-ttu-id="aea6a-121">Virtual Machine Scale Sets zapewnić wysoką dostępność i skalowalność dla aplikacji działających w Virtual Machines.</span><span class="sxs-lookup"><span data-stu-id="aea6a-121">Virtual Machine Scale Sets provide high availability and scalability for applications running in Virtual Machines.</span></span>

### <a name="virtual-machine-size"></a><span data-ttu-id="aea6a-122">Rozmiar maszyny wirtualnej</span><span class="sxs-lookup"><span data-stu-id="aea6a-122">Virtual Machine Size</span></span>

<span data-ttu-id="aea6a-123">Wybierz rozmiar i typ maszyny wirtualnej, która jest optymalnie zoptymalizowana dla obciążenia.</span><span class="sxs-lookup"><span data-stu-id="aea6a-123">Choose the virtual machine size and type that is best optimized for your workload.</span></span> <span data-ttu-id="aea6a-124">Aby uzyskać więcej informacji, zobacz [rozmiary maszyn wirtualnych z systemem Windows na platformie Azure](/azure/virtual-machines/windows/sizes).</span><span class="sxs-lookup"><span data-stu-id="aea6a-124">For more information, see [Sizes for Windows virtual machines in Azure](/azure/virtual-machines/windows/sizes).</span></span>

### <a name="maintenance"></a><span data-ttu-id="aea6a-125">Konserwacja</span><span class="sxs-lookup"><span data-stu-id="aea6a-125">Maintenance</span></span>

<span data-ttu-id="aea6a-126">Podobnie jak w przypadku maszyn lokalnych, użytkownik jest odpowiedzialny za konserwację i aktualizowanie maszyny wirtualnej<sup>&#42;</sup>.</span><span class="sxs-lookup"><span data-stu-id="aea6a-126">Just like an on-premises machine, you are responsible for maintaining and updating the virtual machine<sup>&#42;</sup>.</span></span> <span data-ttu-id="aea6a-127">Jeśli aplikacja może działać w środowisku PaaS (Platform as a Service), takim jak [Azure App Service](/azure/app-service/) lub w [kontenerze](/azure/app-service/containers/), spowoduje to usunięcie tej potrzeby.</span><span class="sxs-lookup"><span data-stu-id="aea6a-127">If your application can run in a Platform as a Service (PaaS) environment such as [Azure App Service](/azure/app-service/) or in a [container](/azure/app-service/containers/), that will remove this need.</span></span>

<span data-ttu-id="aea6a-128">*<sup>&#42;</sup> [automatyczne uaktualnienia systemu operacyjnego dla zestawów skalowania maszyn wirtualnych](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade) jest obecnie dostępne jako usługa w wersji zapoznawczej.*</span><span class="sxs-lookup"><span data-stu-id="aea6a-128">*<sup>&#42;</sup>[Automatic OS upgrades for virtual machine scale sets](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade) is currently available as a Preview service.*</span></span>

### <a name="virtual-networks"></a><span data-ttu-id="aea6a-129">Sieci wirtualne</span><span class="sxs-lookup"><span data-stu-id="aea6a-129">Virtual Networks</span></span>

<span data-ttu-id="aea6a-130">Usługa Azure Virtual Networks umożliwia:</span><span class="sxs-lookup"><span data-stu-id="aea6a-130">Azure Virtual Networks enable you to:</span></span>

- <span data-ttu-id="aea6a-131">Tworzenie infrastruktury hybrydowej kontrolowanej przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="aea6a-131">Build a hybrid infrastructure that you control</span></span>
- <span data-ttu-id="aea6a-132">Przenoszenie własnych adresów IP i serwerów DNS</span><span class="sxs-lookup"><span data-stu-id="aea6a-132">Bring your own IP addresses and DNS servers</span></span>
- <span data-ttu-id="aea6a-133">Tworzenie izolowanego i wysoce bezpiecznego środowiska dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="aea6a-133">Create an isolated and highly secure environment for your applications</span></span>
- <span data-ttu-id="aea6a-134">Połącz maszynę wirtualną z siecią lokalną przy użyciu jednej z kilku [opcji łączności](/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti)</span><span class="sxs-lookup"><span data-stu-id="aea6a-134">Connect your VM to your on-premises network using one of several [connectivity options](/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti)</span></span>
- <span data-ttu-id="aea6a-135">Integruj maszynę wirtualną z siecią lokalną za pomocą [ExpressRoute](https://azure.microsoft.com/services/expressroute/)</span><span class="sxs-lookup"><span data-stu-id="aea6a-135">Integrate your virtual machine into your on-premises network using [ExpressRoute](https://azure.microsoft.com/services/expressroute/)</span></span>

<span data-ttu-id="aea6a-136">Aby rozpocząć, zobacz [dokumentację dotyczącą Virtual Network](/azure/virtual-network/)</span><span class="sxs-lookup"><span data-stu-id="aea6a-136">To get started, see the [Virtual Network documentation](/azure/virtual-network/)</span></span>

### <a name="active-directory"></a><span data-ttu-id="aea6a-137">Active Directory</span><span class="sxs-lookup"><span data-stu-id="aea6a-137">Active Directory</span></span>
<span data-ttu-id="aea6a-138">Wiele aplikacji używa Active Directory do uwierzytelniania i zarządzania tożsamościami.</span><span class="sxs-lookup"><span data-stu-id="aea6a-138">Many applications use Active Directory for authentication and identity management.</span></span>

- <span data-ttu-id="aea6a-139">Azure AD Connect umożliwia integrację katalogów lokalnych z Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="aea6a-139">Azure AD Connect enables you to integrate your on-premises directories with Azure Active Directory.</span></span> <span data-ttu-id="aea6a-140">Aby rozpocząć, zobacz [integrowanie katalogów lokalnych z Azure Active Directory](/azure/active-directory/connect/active-directory-aadconnect).</span><span class="sxs-lookup"><span data-stu-id="aea6a-140">To get started, see [Integrate your on-premises directories with Azure Active Directory](/azure/active-directory/connect/active-directory-aadconnect).</span></span>
- <span data-ttu-id="aea6a-141">Alternatywnie [ExpressRoute](https://azure.microsoft.com/services/expressroute/) umożliwia aplikacji dostęp do Active Directory lokalnych.</span><span class="sxs-lookup"><span data-stu-id="aea6a-141">Alternatively, [ExpressRoute](https://azure.microsoft.com/services/expressroute/) enables your application to access your on-premises Active Directory.</span></span>

### <a name="sql-databases"></a><span data-ttu-id="aea6a-142">Bazy danych SQL</span><span class="sxs-lookup"><span data-stu-id="aea6a-142">SQL Databases</span></span>

<span data-ttu-id="aea6a-143">Jeśli aplikacja korzysta z lokalnej bazy danych, aplikacja nie będzie mogła komunikować się z nią domyślnie.</span><span class="sxs-lookup"><span data-stu-id="aea6a-143">If your application is using an on-premises database, your app will not be able to talk to it by default.</span></span> <span data-ttu-id="aea6a-144">Można:</span><span class="sxs-lookup"><span data-stu-id="aea6a-144">You can either:</span></span>

- <span data-ttu-id="aea6a-145">Skonfiguruj sieć hybrydową, która umożliwia aplikacji dostęp do bazy danych działającej lokalnie.</span><span class="sxs-lookup"><span data-stu-id="aea6a-145">Configure a hybrid network that enables your application to access your database running on-premises.</span></span>
- <span data-ttu-id="aea6a-146">Przeprowadź migrację bazy danych do platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="aea6a-146">Migrate your database to the Azure.</span></span> <span data-ttu-id="aea6a-147">Aby uzyskać więcej informacji, zobacz [Migrowanie bazy danych SQL Server na platformę Azure](sql.md).</span><span class="sxs-lookup"><span data-stu-id="aea6a-147">For more information, see [Migrate your SQL Server database to Azure](sql.md).</span></span>

### <a name="high-availability-and-scalability"></a><span data-ttu-id="aea6a-148">Wysoka dostępność i skalowalność</span><span class="sxs-lookup"><span data-stu-id="aea6a-148">High Availability and Scalability</span></span>

#### <a name="virtual-machine-scale-sets"></a><span data-ttu-id="aea6a-149">Usługa Virtual Machine Scale Sets</span><span class="sxs-lookup"><span data-stu-id="aea6a-149">Virtual Machine Scale Sets</span></span>
<span data-ttu-id="aea6a-150">Upewnij się, że aplikacja jest wysoce dostępna i można ją skalować, migrować do zestawu skalowania maszyn wirtualnych platformy Azure, aby zwiększyć dostępność i skalowalność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aea6a-150">You want to make sure that your application is highly available and can scale, migrate your VM image to an Azure Virtual Machine Scale Set to improve the availability and scalability of your application.</span></span> <span data-ttu-id="aea6a-151">VM Scale Sets zapewnić możliwość korzystania z istniejącej maszyny wirtualnej, która została już skonfigurowana, lub skonfigurowania potoku kompilacji w celu utworzenia obrazu w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aea6a-151">VM Scale Sets provide the ability to use an existing VM you've already configured or set up a build pipeline to build an image with your application.</span></span>

<span data-ttu-id="aea6a-152">Aby rozpocząć, zobacz [wdrażanie aplikacji w zestawach skalowania maszyn wirtualnych](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app).</span><span class="sxs-lookup"><span data-stu-id="aea6a-152">To get started, see [Deploy your application on virtual machine scale sets](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app).</span></span>

#### <a name="centralized-logging"></a><span data-ttu-id="aea6a-153">Scentralizowane rejestrowanie</span><span class="sxs-lookup"><span data-stu-id="aea6a-153">Centralized Logging</span></span>
<span data-ttu-id="aea6a-154">W przypadku uruchamiania aplikacji w wielu wystąpieniach warto rozważyć przechowywanie dzienników w scentralizowanej lokalizacji, takiej jak [usługa Azure Storage](/azure/storage/).</span><span class="sxs-lookup"><span data-stu-id="aea6a-154">When running your application across multiple instances, consider storing your logs in a centralized location such as [Azure Storage](/azure/storage/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="aea6a-155">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="aea6a-155">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="aea6a-156">Migrowanie bazy danych programu SQL Server na platformę Azure</span><span class="sxs-lookup"><span data-stu-id="aea6a-156">Migrate a SQL Server database to Azure</span></span>](sql.md)
