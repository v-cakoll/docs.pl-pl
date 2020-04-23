---
title: Migrowanie aplikacji sieci Web ASP.NET na maszynę wirtualną platformy Azure
description: Dowiedz się, jak przeprowadzić migrację ASP.NET aplikacji sieci Web z lokalnego urządzenia do maszyny wirtualnej platformy Azure.
ms.topic: how-to
ms.date: 11/15/2017
ms.openlocfilehash: cc9477de92e6105762636ed3a2241949e69ac8ea
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "82072124"
---
# <a name="migrate-an-aspnet-web-application-to-an-azure-virtual-machine"></a><span data-ttu-id="7170d-103">Migrowanie aplikacji sieci Web ASP.NET do maszyny wirtualnej platformy Azure</span><span class="sxs-lookup"><span data-stu-id="7170d-103">Migrate an ASP.NET Web application to an Azure Virtual Machine</span></span>

<span data-ttu-id="7170d-104">Ten dokument zawiera omówienie sposobu migracji ASP.NET aplikacji sieci web z lokalnego do maszyny wirtualnej platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="7170d-104">This document provides an overview of how to migrate an ASP.NET web application from on-premises to an Azure Virtual Machine.</span></span>

## <a name="quickstart"></a><span data-ttu-id="7170d-105">Szybki start</span><span class="sxs-lookup"><span data-stu-id="7170d-105">Quickstart</span></span>

<span data-ttu-id="7170d-106">Dowiedz się, jak utworzyć maszynę wirtualną i opublikować w niej aplikację: [publikowanie na maszynie wirtualnej platformy Azure](https://tutorials.visualstudio.com/aspnet-vm/intro)</span><span class="sxs-lookup"><span data-stu-id="7170d-106">Learn how to create a virtual machine and publish your app to it: [Publish to an Azure VM](https://tutorials.visualstudio.com/aspnet-vm/intro)</span></span>

## <a name="get-started"></a><span data-ttu-id="7170d-107">Rozpoczęcie pracy</span><span class="sxs-lookup"><span data-stu-id="7170d-107">Get Started</span></span>

<span data-ttu-id="7170d-108">Te samouczki pokazują kroki tworzenia (lub migracji) maszyny wirtualnej, publikowania aplikacji sieci web do niej i innych zadań, które mogą być wymagane do obsługi aplikacji na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="7170d-108">These tutorials demonstrate the steps to create (or migrate) a virtual machine, publish your web application to it, and other tasks that may be required to support your application in Azure.</span></span>

- <span data-ttu-id="7170d-109">Utwórz maszynę wirtualną dla aplikacji ASP.NET na platformie Azure, korzystając z jednej z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="7170d-109">Create a virtual machine for your ASP.NET application in Azure using one of the following options:</span></span>
  - [<span data-ttu-id="7170d-110">Tworzenie nowej maszyny wirtualnej dla aplikacji ASP.NET</span><span class="sxs-lookup"><span data-stu-id="7170d-110">Create a new virtual machine for ASP.NET Applications</span></span>](https://go.microsoft.com/fwlink/?linkid=863237)
  - [<span data-ttu-id="7170d-111">Migrowanie istniejącej lokalnej maszyny wirtualnej VMWare</span><span class="sxs-lookup"><span data-stu-id="7170d-111">Migrate an existing on-premises VMWare virtual machine</span></span>](https://docs.microsoft.com/azure/migrate/tutorial-migrate-vmware)
  - [<span data-ttu-id="7170d-112">Migrowanie istniejącej lokalnej maszyny wirtualnej funkcji Hyper-V</span><span class="sxs-lookup"><span data-stu-id="7170d-112">Migrate an existing on-premises Hyper-V virtual machine</span></span>](https://docs.microsoft.com/azure/migrate/tutorial-migrate-hyper-v)
- [<span data-ttu-id="7170d-113">Publikowanie aplikacji przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7170d-113">Publish your app using Visual Studio</span></span>](https://go.microsoft.com/fwlink/?linkid=863240)
- [<span data-ttu-id="7170d-114">Tworzenie bezpiecznej sieci wirtualnej dla maszyn wirtualnych</span><span class="sxs-lookup"><span data-stu-id="7170d-114">Create a secure virtual network for your VMs</span></span>](https://docs.microsoft.com/azure/virtual-network/virtual-network-get-started-vnet-subnet)
- [<span data-ttu-id="7170d-115">Tworzenie potoku ciągłej integracji/ciągłego wdrażania dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="7170d-115">Create a CI/CD pipeline for your application</span></span>](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-webdeploy-iis-deploygroups)
- [<span data-ttu-id="7170d-116">Przejście do zestawu skalowania maszyny Wirtualnej w celu zapewnienia wysokiej dostępności i skalowalności</span><span class="sxs-lookup"><span data-stu-id="7170d-116">Move to a VM scale set for high availability and scalability</span></span>](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)

## <a name="considerations"></a><span data-ttu-id="7170d-117">Zagadnienia do rozważenia</span><span class="sxs-lookup"><span data-stu-id="7170d-117">Considerations</span></span>

### <a name="benefits"></a><span data-ttu-id="7170d-118">Korzyści</span><span class="sxs-lookup"><span data-stu-id="7170d-118">Benefits</span></span>

<span data-ttu-id="7170d-119">Maszyny wirtualne oferują najłatwiejszą ścieżkę do migracji aplikacji z lokalnego do chmury.</span><span class="sxs-lookup"><span data-stu-id="7170d-119">Virtual machines offer the easiest path to migrate an application from on-premises to the cloud.</span></span> <span data-ttu-id="7170d-120">Umożliwiają one replikację tego samego środowiska, którego aplikacja używa lokalnie, eliminując jednocześnie konieczność obsługi własnych centrów danych.</span><span class="sxs-lookup"><span data-stu-id="7170d-120">They enable you to replicate the same environment your application uses on-premises, while removing the need to maintain your own data centers.</span></span> <span data-ttu-id="7170d-121">Zestawy skalowania maszyny wirtualnej zapewniają wysoką dostępność i skalowalność aplikacji działających na maszynach wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="7170d-121">Virtual Machine Scale Sets provide high availability and scalability for applications running in Virtual Machines.</span></span>

### <a name="virtual-machine-size"></a><span data-ttu-id="7170d-122">Rozmiar maszyny wirtualnej</span><span class="sxs-lookup"><span data-stu-id="7170d-122">Virtual Machine Size</span></span>

<span data-ttu-id="7170d-123">Wybierz rozmiar i typ maszyny wirtualnej, który jest najlepiej zoptymalizowany pod kątem obciążenia.</span><span class="sxs-lookup"><span data-stu-id="7170d-123">Choose the virtual machine size and type that is best optimized for your workload.</span></span> <span data-ttu-id="7170d-124">Aby uzyskać więcej informacji, zobacz [Rozmiary maszyn wirtualnych systemu Windows na platformie Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sizes).</span><span class="sxs-lookup"><span data-stu-id="7170d-124">For more information, see [Sizes for Windows virtual machines in Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sizes).</span></span>

### <a name="maintenance"></a><span data-ttu-id="7170d-125">Konserwacja</span><span class="sxs-lookup"><span data-stu-id="7170d-125">Maintenance</span></span>

<span data-ttu-id="7170d-126">Podobnie jak na komputerze lokalnym, jesteś odpowiedzialny za utrzymanie i aktualizację maszyny wirtualnej<sup>&#42;</sup>.</span><span class="sxs-lookup"><span data-stu-id="7170d-126">Just like an on-premises machine, you are responsible for maintaining and updating the virtual machine<sup>&#42;</sup>.</span></span> <span data-ttu-id="7170d-127">Jeśli aplikacja może działać w środowisku platformy jako usługi (PaaS), takich jak [usługa Azure App Service](https://docs.microsoft.com/azure/app-service/) lub w [kontenerze,](https://docs.microsoft.com/azure/app-service/containers/)które usuną tę potrzebę.</span><span class="sxs-lookup"><span data-stu-id="7170d-127">If your application can run in a Platform as a Service (PaaS) environment such as [Azure App Service](https://docs.microsoft.com/azure/app-service/) or in a [container](https://docs.microsoft.com/azure/app-service/containers/), that will remove this need.</span></span>

<span data-ttu-id="7170d-128">*<sup>&#42;</sup> [Automatyczne uaktualnienia systemu operacyjnego dla zestawów skalowania maszyny wirtualnej](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade) są obecnie dostępne jako usługa w wersji zapoznawczej.*</span><span class="sxs-lookup"><span data-stu-id="7170d-128">*<sup>&#42;</sup>[Automatic OS upgrades for virtual machine scale sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade) is currently available as a Preview service.*</span></span>

### <a name="virtual-networks"></a><span data-ttu-id="7170d-129">Sieci wirtualne</span><span class="sxs-lookup"><span data-stu-id="7170d-129">Virtual Networks</span></span>

<span data-ttu-id="7170d-130">Sieci wirtualne platformy Azure umożliwiają:</span><span class="sxs-lookup"><span data-stu-id="7170d-130">Azure Virtual Networks enable you to:</span></span>

- <span data-ttu-id="7170d-131">Tworzenie kontrolowanej infrastruktury hybrydowej</span><span class="sxs-lookup"><span data-stu-id="7170d-131">Build a hybrid infrastructure that you control</span></span>
- <span data-ttu-id="7170d-132">Przynieś własne adresy IP i serwery DNS</span><span class="sxs-lookup"><span data-stu-id="7170d-132">Bring your own IP addresses and DNS servers</span></span>
- <span data-ttu-id="7170d-133">Tworzenie odizolowanego i wysoce bezpiecznego środowiska dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="7170d-133">Create an isolated and highly secure environment for your applications</span></span>
- <span data-ttu-id="7170d-134">Łączenie maszyny wirtualnej z siecią lokalną przy użyciu jednej z kilku [opcji łączności](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti)</span><span class="sxs-lookup"><span data-stu-id="7170d-134">Connect your VM to your on-premises network using one of several [connectivity options](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti)</span></span>
- <span data-ttu-id="7170d-135">Integracja maszyny wirtualnej z siecią lokalną przy użyciu usługi [ExpressRoute](https://azure.microsoft.com/services/expressroute/)</span><span class="sxs-lookup"><span data-stu-id="7170d-135">Integrate your virtual machine into your on-premises network using [ExpressRoute](https://azure.microsoft.com/services/expressroute/)</span></span>

<span data-ttu-id="7170d-136">Aby rozpocząć, zapoznaj się z [dokumentacją sieci wirtualnej](https://docs.microsoft.com/azure/virtual-network/)</span><span class="sxs-lookup"><span data-stu-id="7170d-136">To get started, see the [Virtual Network documentation](https://docs.microsoft.com/azure/virtual-network/)</span></span>

### <a name="active-directory"></a><span data-ttu-id="7170d-137">Usługa Active Directory</span><span class="sxs-lookup"><span data-stu-id="7170d-137">Active Directory</span></span>
<span data-ttu-id="7170d-138">Wiele aplikacji używa usługi Active Directory do uwierzytelniania i zarządzania tożsamościami.</span><span class="sxs-lookup"><span data-stu-id="7170d-138">Many applications use Active Directory for authentication and identity management.</span></span>

- <span data-ttu-id="7170d-139">Usługa Azure AD Connect umożliwia integrację katalogów lokalnych z usługą Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="7170d-139">Azure AD Connect enables you to integrate your on-premises directories with Azure Active Directory.</span></span> <span data-ttu-id="7170d-140">Aby rozpocząć, zobacz [Integrowanie katalogów lokalnych z usługą Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).</span><span class="sxs-lookup"><span data-stu-id="7170d-140">To get started, see [Integrate your on-premises directories with Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).</span></span>
- <span data-ttu-id="7170d-141">Alternatywnie [usługa ExpressRoute](https://azure.microsoft.com/services/expressroute/) umożliwia aplikacji dostęp do lokalnej usługi Active Directory.</span><span class="sxs-lookup"><span data-stu-id="7170d-141">Alternatively, [ExpressRoute](https://azure.microsoft.com/services/expressroute/) enables your application to access your on-premises Active Directory.</span></span>

### <a name="sql-databases"></a><span data-ttu-id="7170d-142">Bazy danych SQL</span><span class="sxs-lookup"><span data-stu-id="7170d-142">SQL Databases</span></span>

<span data-ttu-id="7170d-143">Jeśli aplikacja korzysta z lokalnej bazy danych, aplikacja nie będzie mogła domyślnie z nią rozmawiać.</span><span class="sxs-lookup"><span data-stu-id="7170d-143">If your application is using an on-premises database, your app will not be able to talk to it by default.</span></span> <span data-ttu-id="7170d-144">Można:</span><span class="sxs-lookup"><span data-stu-id="7170d-144">You can either:</span></span>

- <span data-ttu-id="7170d-145">Skonfiguruj sieć hybrydową, która umożliwia aplikacji dostęp do bazy danych działającej lokalnie.</span><span class="sxs-lookup"><span data-stu-id="7170d-145">Configure a hybrid network that enables your application to access your database running on-premises.</span></span>
- <span data-ttu-id="7170d-146">Migrowanie bazy danych na platformę Azure.</span><span class="sxs-lookup"><span data-stu-id="7170d-146">Migrate your database to the Azure.</span></span> <span data-ttu-id="7170d-147">Aby uzyskać więcej informacji, zobacz [Migrowanie bazy danych programu SQL Server na platformę Azure](sql.md).</span><span class="sxs-lookup"><span data-stu-id="7170d-147">For more information, see [Migrate your SQL Server database to Azure](sql.md).</span></span>

### <a name="high-availability-and-scalability"></a><span data-ttu-id="7170d-148">Wysoka dostępność i skalowalność</span><span class="sxs-lookup"><span data-stu-id="7170d-148">High Availability and Scalability</span></span>

#### <a name="virtual-machine-scale-sets"></a><span data-ttu-id="7170d-149">Zestawy skali maszyn wirtualnych</span><span class="sxs-lookup"><span data-stu-id="7170d-149">Virtual Machine Scale Sets</span></span>
<span data-ttu-id="7170d-150">Chcesz upewnić się, że aplikacja jest wysoce dostępna i można skalować, migrować obraz maszyny wirtualnej do zestawu skalowania maszyny wirtualnej platformy Azure, aby zwiększyć dostępność i skalowalność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7170d-150">You want to make sure that your application is highly available and can scale, migrate your VM image to an Azure Virtual Machine Scale Set to improve the availability and scalability of your application.</span></span> <span data-ttu-id="7170d-151">Zestawy skalowania maszyny Wirtualnej zapewniają możliwość używania istniejącej maszyny Wirtualnej, która została już skonfigurowana lub skonfigurowania potoku kompilacji w celu utworzenia obrazu za pomocą aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7170d-151">VM Scale Sets provide the ability to use an existing VM you've already configured or set up a build pipeline to build an image with your application.</span></span>

<span data-ttu-id="7170d-152">Aby rozpocząć, zobacz [Wdrażanie aplikacji w zestawach skalowania maszyny wirtualnej](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app).</span><span class="sxs-lookup"><span data-stu-id="7170d-152">To get started, see [Deploy your application on virtual machine scale sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app).</span></span>

#### <a name="centralized-logging"></a><span data-ttu-id="7170d-153">Scentralizowane rejestrowanie</span><span class="sxs-lookup"><span data-stu-id="7170d-153">Centralized Logging</span></span>
<span data-ttu-id="7170d-154">Podczas uruchamiania aplikacji w wielu wystąpieniach należy rozważyć przechowywanie dzienników w scentralizowanej lokalizacji, takiej jak [usługa Azure Storage.](https://docs.microsoft.com/azure/storage/)</span><span class="sxs-lookup"><span data-stu-id="7170d-154">When running your application across multiple instances, consider storing your logs in a centralized location such as [Azure Storage](https://docs.microsoft.com/azure/storage/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="7170d-155">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="7170d-155">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7170d-156">Migrowanie bazy danych programu SQL Server na platformę Azure</span><span class="sxs-lookup"><span data-stu-id="7170d-156">Migrate a SQL Server database to Azure</span></span>](sql.md)
