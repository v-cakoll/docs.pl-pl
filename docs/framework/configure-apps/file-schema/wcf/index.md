---
title: Schemat konfiguracji programu WCF
ms.date: 03/30/2017
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
ms.openlocfilehash: 8d7b4cbad1876888e7a22a92bdb28a17b880e159
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925392"
---
# <a name="wcf-configuration-schema"></a><span data-ttu-id="eb22b-102">Schemat konfiguracji programu WCF</span><span class="sxs-lookup"><span data-stu-id="eb22b-102">WCF Configuration Schema</span></span>
<span data-ttu-id="eb22b-103">Elementy konfiguracji programu Windows Communication Foundation (WCF) umożliwiają skonfigurowanie usług i aplikacji klienckich platformy WCF.</span><span class="sxs-lookup"><span data-stu-id="eb22b-103">Windows Communication Foundation (WCF) configuration elements enable you to configure WCF service and client applications.</span></span> <span data-ttu-id="eb22b-104">Aby tworzyć i modyfikować pliki konfiguracji dla klientów i usług, można użyć [Narzędzia Edytora konfiguracji (SvcConfigEditor. exe)](../../../wcf/configuration-editor-tool-svcconfigeditor-exe.md) .</span><span class="sxs-lookup"><span data-stu-id="eb22b-104">You can use the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../wcf/configuration-editor-tool-svcconfigeditor-exe.md) to create and modify configuration files for clients and services.</span></span> <span data-ttu-id="eb22b-105">Ponieważ pliki konfiguracji są sformatowane jako XML, należy zapoznać się z kodem XML, aby ręcznie edytować je za pomocą edytora tekstu.</span><span class="sxs-lookup"><span data-stu-id="eb22b-105">Since the configuration files are formatted as XML, you must be familiar with XML if you want to manually edit them using a text editor.</span></span> <span data-ttu-id="eb22b-106">W przeciwnym razie może wystąpić problemy, takie jak unfound tagu elementu XML lub atrybut.</span><span class="sxs-lookup"><span data-stu-id="eb22b-106">Otherwise, you may run into issues such as an unfound XML element tag or attribute.</span></span> <span data-ttu-id="eb22b-107">Wynika to z tagów elementu XML i atrybutów jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="eb22b-107">This is because XML element tags and attributes are case-sensitive.</span></span>  
  
 <span data-ttu-id="eb22b-108">System konfiguracji WCF jest oparty na <xref:System.Configuration> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="eb22b-108">The WCF configuration system is based on the <xref:System.Configuration> namespace.</span></span> <span data-ttu-id="eb22b-109">W związku z tym możesz użyć wszystkich funkcji standardowych dostępnych <xref:System.Configuration> w przestrzeni nazw, takich jak blokowanie konfiguracji, szyfrowanie i scalanie, aby zwiększyć bezpieczeństwo aplikacji i jej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="eb22b-109">Therefore, you can use all the standard features provided by the <xref:System.Configuration> namespace, such as configuration locking, encryption and merging to increase the security of your application and its configuration.</span></span> <span data-ttu-id="eb22b-110">Aby uzyskać więcej informacji na temat tych pojęć, zobacz następujące tematy.</span><span class="sxs-lookup"><span data-stu-id="eb22b-110">For more information on these concepts, see the following topics.</span></span>  
  
 [<span data-ttu-id="eb22b-111">Szyfrowanie informacji o konfiguracji</span><span class="sxs-lookup"><span data-stu-id="eb22b-111">Encrypting Configuration Information</span></span>](https://go.microsoft.com/fwlink/?LinkId=95337)  
  
 [<span data-ttu-id="eb22b-112">Blokowanie ustawień konfiguracji</span><span class="sxs-lookup"><span data-stu-id="eb22b-112">Locking Configuration Settings</span></span>](https://go.microsoft.com/fwlink/?LinkId=95338)  
  
 <span data-ttu-id="eb22b-113">W tej sekcji opisano wszystkie możliwe wartości poszczególnych elementów konfiguracji oraz sposób współdziałania z innymi elementami konfiguracji WCF.</span><span class="sxs-lookup"><span data-stu-id="eb22b-113">This section describes all possible values of each configuration item, and how it interacts with other WCF configuration elements.</span></span> <span data-ttu-id="eb22b-114">Poniższa mapa ilustruje Schemat konfiguracji programu WCF:</span><span class="sxs-lookup"><span data-stu-id="eb22b-114">The following map illustrates the WCF configuration schema:</span></span>  
  
 ![Diagram przedstawiający Schemat konfiguracji programu WCF.](./media/index/windows-communication-foundation-configuration-schema.gif)  
  
> [!CAUTION]
>  <span data-ttu-id="eb22b-116">Należy chronić sekcje konfiguracyjne programu WCF w plikach konfiguracji aplikacji (App. config) za pomocą odpowiednich list Access Control (ACL), aby zapobiec potencjalnym zagrożeniom bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="eb22b-116">You should protect WCF configuration sections in your application configuration files (app.config) with appropriate Access Control Lists (ACL) to prevent any potential security threats.</span></span>  <span data-ttu-id="eb22b-117">Należy na przykład upewnić się, że tylko odpowiednie osoby mają dostęp do ustawień zabezpieczeń powiązań aplikacji lub je modyfikować, a także w sekcji model usługi w pliku konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="eb22b-117">For example, you should make sure that only the appropriate people can access or modify the security settings on application bindings, or the service model section of the configuration file for a service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eb22b-118">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="eb22b-118">In This Section</span></span>  
 [<span data-ttu-id="eb22b-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="eb22b-119">\<system.serviceModel></span></span>](system-servicemodel.md)  
 <span data-ttu-id="eb22b-120">Opisuje `ServiceModel` elementu.</span><span class="sxs-lookup"><span data-stu-id="eb22b-120">Describes the `ServiceModel` element.</span></span>  
  
 [<span data-ttu-id="eb22b-121">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="eb22b-121">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)  
 <span data-ttu-id="eb22b-122">Konfiguruje narzędzie SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="eb22b-122">Configures the SMSvcHost.exe tool.</span></span>  
  
 [<span data-ttu-id="eb22b-123">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="eb22b-123">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)  
 <span data-ttu-id="eb22b-124">Element najwyższego poziomu służący do ustawiania opcji przy użyciu serializatorów, <xref:System.Runtime.Serialization.DataContractSerializer>takich jak.</span><span class="sxs-lookup"><span data-stu-id="eb22b-124">The top-level element for setting options when using serializers such as the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="eb22b-125">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="eb22b-125">Related Sections</span></span>  
 [<span data-ttu-id="eb22b-126">Konfigurowanie aplikacji Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="eb22b-126">Configuring Windows Communication Foundation Applications</span></span>](../../../wcf/configuring-services.md)  
 <span data-ttu-id="eb22b-127">Opisuje sposób konfigurowania usług i klientów programu WCF.</span><span class="sxs-lookup"><span data-stu-id="eb22b-127">Describes how to configure WCF services and clients.</span></span>
