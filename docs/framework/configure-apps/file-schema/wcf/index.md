---
title: Schemat konfiguracji programu WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 05aeeea7d10c012804fe083890bcc8516aa8c8bc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="wcf-configuration-schema"></a><span data-ttu-id="3540e-102">Schemat konfiguracji programu WCF</span><span class="sxs-lookup"><span data-stu-id="3540e-102">WCF Configuration Schema</span></span>
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="3540e-103">elementy konfiguracji umożliwiają skonfigurowanie [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usługi i aplikacje klienckie.</span><span class="sxs-lookup"><span data-stu-id="3540e-103"> configuration elements enable you to configure [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service and client applications.</span></span> <span data-ttu-id="3540e-104">Można użyć [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) pozwala tworzyć i modyfikować pliki konfiguracyjne dla klientów i usług.</span><span class="sxs-lookup"><span data-stu-id="3540e-104">You can use the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) to create and modify configuration files for clients and services.</span></span> <span data-ttu-id="3540e-105">Ponieważ pliki konfiguracji są w formacie XML, należy zapoznać się z XML, jeśli chcesz ręcznie edytować za pomocą edytora tekstu.</span><span class="sxs-lookup"><span data-stu-id="3540e-105">Since the configuration files are formatted as XML, you must be familiar with XML if you want to manually edit them using a text editor.</span></span> <span data-ttu-id="3540e-106">W przeciwnym razie może wystąpić problemy, takie jak unfound tagu elementu XML lub atrybut.</span><span class="sxs-lookup"><span data-stu-id="3540e-106">Otherwise, you may run into issues such as an unfound XML element tag or attribute.</span></span> <span data-ttu-id="3540e-107">Wynika to z tagów elementu XML i atrybutów jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="3540e-107">This is because XML element tags and attributes are case-sensitive.</span></span>  
  
 <span data-ttu-id="3540e-108">[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Konfiguracji system jest oparty na <xref:System.Configuration> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3540e-108">The [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] configuration system is based on the <xref:System.Configuration> namespace.</span></span> <span data-ttu-id="3540e-109">W takim przypadku używane standardowe funkcje oferowane przez <xref:System.Configuration> przestrzeni nazw, takie jak konfiguracja, blokowanie, szyfrowania i scalanie, aby zwiększyć bezpieczeństwo aplikacji i jej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3540e-109">Therefore, you can use all the standard features provided by the <xref:System.Configuration> namespace, such as configuration locking, encryption and merging to increase the security of your application and its configuration.</span></span> <span data-ttu-id="3540e-110">Aby uzyskać więcej informacji dotyczących tych pojęć zobacz następujące tematy.</span><span class="sxs-lookup"><span data-stu-id="3540e-110">For more information on these concepts, see the following topics.</span></span>  
  
 [<span data-ttu-id="3540e-111">Szyfrowanie informacji o konfiguracji</span><span class="sxs-lookup"><span data-stu-id="3540e-111">Encrypting Configuration Information</span></span>](http://go.microsoft.com/fwlink/?LinkId=95337)  
  
 [<span data-ttu-id="3540e-112">Ustawienia konfiguracji blokowania</span><span class="sxs-lookup"><span data-stu-id="3540e-112">Locking Configuration Settings</span></span>](http://go.microsoft.com/fwlink/?LinkId=95338)  
  
 <span data-ttu-id="3540e-113">W tej sekcji opisano wszystkie możliwe wartości poszczególnych elementów konfiguracji i jak współdziała z innymi elementami konfiguracji usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="3540e-113">This section describes all possible values of each configuration item, and how it interacts with other WCF configuration elements.</span></span> <span data-ttu-id="3540e-114">Następujące mapy przedstawiono schemat konfiguracji usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="3540e-114">The following map illustrates the WCF configuration schema.</span></span>  
  
 <span data-ttu-id="3540e-115">![Schemat konfiguracji programu WCF](../../../../../docs/framework/configure-apps/file-schema/wcf/media/orcasconfigschema.gif "OrcasConfigSchema")</span><span class="sxs-lookup"><span data-stu-id="3540e-115">![WCF Configuration Schema](../../../../../docs/framework/configure-apps/file-schema/wcf/media/orcasconfigschema.gif "OrcasConfigSchema")</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="3540e-116">Należy chronić [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] sekcji konfiguracyjnych w plikach konfiguracji aplikacji (app.config) z odpowiednią kontroli dostępu zawiera listę (ACL) aby uniemożliwić wszystkie potencjalne zagrożenia bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="3540e-116">You should protect [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] configuration sections in your application configuration files (app.config) with appropriate Access Control Lists (ACL) to prevent any potential security threats.</span></span>  <span data-ttu-id="3540e-117">Należy na przykład upewnij się, że odpowiednie osoby mogą uzyskać dostęp lub zmodyfikować ustawienia zabezpieczeń na powiązania aplikacji lub modelu usługi części pliku konfiguracji dla usługi.</span><span class="sxs-lookup"><span data-stu-id="3540e-117">For example, you should make sure that only the appropriate people can access or modify the security settings on application bindings, or the service model section of the configuration file for a service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3540e-118">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="3540e-118">In This Section</span></span>  
 [<span data-ttu-id="3540e-119">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="3540e-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
 <span data-ttu-id="3540e-120">Opisuje `ServiceModel` elementu.</span><span class="sxs-lookup"><span data-stu-id="3540e-120">Describes the `ServiceModel` element.</span></span>  
  
 [<span data-ttu-id="3540e-121">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="3540e-121">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)  
 <span data-ttu-id="3540e-122">Konfiguruje narzędzia SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="3540e-122">Configures the SMSvcHost.exe tool.</span></span>  
  
 [<span data-ttu-id="3540e-123">\<System.Runtime.serialization ></span><span class="sxs-lookup"><span data-stu-id="3540e-123">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
 <span data-ttu-id="3540e-124">Element najwyższego poziomu do ustawiania opcji, gdy przy użyciu serializatorów, takich jak <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="3540e-124">The top-level element for setting options when using serializers such as the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3540e-125">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="3540e-125">Related Sections</span></span>  
 [<span data-ttu-id="3540e-126">Konfigurowanie systemu Windows Communication Foundation aplikacji</span><span class="sxs-lookup"><span data-stu-id="3540e-126">Configuring Windows Communication Foundation Applications</span></span>](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 <span data-ttu-id="3540e-127">Opisuje sposób konfigurowania [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usług i klientów.</span><span class="sxs-lookup"><span data-stu-id="3540e-127">Describes how to configure [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services and clients.</span></span>
