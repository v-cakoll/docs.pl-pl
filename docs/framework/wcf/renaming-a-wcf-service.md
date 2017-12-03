---
title: "Zmienianie nazwy usługi WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c2ecd78a7d72b86460f4d1972c42c8550010f02
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="renaming-a-wcf-service"></a><span data-ttu-id="b9ffe-102">Zmienianie nazwy usługi WCF</span><span class="sxs-lookup"><span data-stu-id="b9ffe-102">Renaming a WCF Service</span></span>
<span data-ttu-id="b9ffe-103">W tym temacie opisano, jak można zmienić nazwy [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="b9ffe-103">This topic describes how you can rename a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service.</span></span>  
  
## <a name="renaming-a-wcf-service"></a><span data-ttu-id="b9ffe-104">Zmienianie nazwy usługi WCF</span><span class="sxs-lookup"><span data-stu-id="b9ffe-104">Renaming a WCF Service</span></span>  
 <span data-ttu-id="b9ffe-105">Wykonaj poniższe kroki, aby zmienić nazwę usługi w programie [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] szablonu,</span><span class="sxs-lookup"><span data-stu-id="b9ffe-105">Perform the following steps to rename a service in a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] template,</span></span>  
  
-   <span data-ttu-id="b9ffe-106">Zmień nazwę klasy, która implementuje usługę.</span><span class="sxs-lookup"><span data-stu-id="b9ffe-106">Change the name of the class that implements the service.</span></span>  
  
-   <span data-ttu-id="b9ffe-107">W pliku konfiguracji usługi Zmień nazwę usługi na nową nazwę, którą wybrano, jak wskazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b9ffe-107">In the configuration file of the service, change the name of the service to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="b9ffe-108">Może to być plik konfiguracji pliku app.config lub web.config, w zależności od modelu hostingu.</span><span class="sxs-lookup"><span data-stu-id="b9ffe-108">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
-   <span data-ttu-id="b9ffe-109">Czy usługa jest webhosted, używa plik *.svc.</span><span class="sxs-lookup"><span data-stu-id="b9ffe-109">If your service is webhosted, it uses an *.svc file.</span></span> <span data-ttu-id="b9ffe-110">Otwórz plik svc i zmodyfikować nazwę usługi, jak wskazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b9ffe-110">Open the svc file and modify the name of your service as indicated in the following example.</span></span> <span data-ttu-id="b9ffe-111">Ten krok nie jest konieczne własnym obsługiwanych aplikacji, ponieważ nie ma żadnego pliku svc.</span><span class="sxs-lookup"><span data-stu-id="b9ffe-111">This step is not necessary for self-hosted applications, as there is no svc file.</span></span>  
  
```  
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a><span data-ttu-id="b9ffe-112">Zmiana nazwy kontraktu usługi WCF</span><span class="sxs-lookup"><span data-stu-id="b9ffe-112">Renaming a WCF Service Contract</span></span>  
  
-   <span data-ttu-id="b9ffe-113">Wykonaj poniższe kroki, aby zmienić nazwę kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="b9ffe-113">Perform the following steps to rename the service contract,</span></span>  
  
-   <span data-ttu-id="b9ffe-114">Zmień nazwę kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="b9ffe-114">Change the name of the service contract.</span></span>  
  
-   <span data-ttu-id="b9ffe-115">W pliku konfiguracji usługi należy zmienić nazwę kontraktu usługi na nową nazwę, którą wybrano, jak wskazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b9ffe-115">In the configuration file of the service, change the name of the service contract to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="b9ffe-116">Może to być plik konfiguracji pliku app.config lub web.config, w zależności od modelu hostingu.</span><span class="sxs-lookup"><span data-stu-id="b9ffe-116">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
