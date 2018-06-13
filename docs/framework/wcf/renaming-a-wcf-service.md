---
title: Zmienianie nazwy usługi WCF
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: a215523b92757e3bde1dae2e50de22169020e870
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498990"
---
# <a name="renaming-a-wcf-service"></a><span data-ttu-id="63b94-102">Zmienianie nazwy usługi WCF</span><span class="sxs-lookup"><span data-stu-id="63b94-102">Renaming a WCF Service</span></span>
<span data-ttu-id="63b94-103">W tym temacie opisano, jak można zmienić nazwy usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="63b94-103">This topic describes how you can rename a Windows Communication Foundation (WCF) service.</span></span>  
  
## <a name="renaming-a-wcf-service"></a><span data-ttu-id="63b94-104">Zmienianie nazwy usługi WCF</span><span class="sxs-lookup"><span data-stu-id="63b94-104">Renaming a WCF Service</span></span>  
 <span data-ttu-id="63b94-105">Wykonaj poniższe kroki, aby zmienić nazwę usługi w szablonie usługi Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="63b94-105">Perform the following steps to rename a service in a Windows Communication Foundation (WCF) template,</span></span>  
  
-   <span data-ttu-id="63b94-106">Zmień nazwę klasy, która implementuje usługę.</span><span class="sxs-lookup"><span data-stu-id="63b94-106">Change the name of the class that implements the service.</span></span>  
  
-   <span data-ttu-id="63b94-107">W pliku konfiguracji usługi Zmień nazwę usługi na nową nazwę, którą wybrano, jak wskazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="63b94-107">In the configuration file of the service, change the name of the service to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="63b94-108">Może to być plik konfiguracji pliku app.config lub web.config, w zależności od modelu hostingu.</span><span class="sxs-lookup"><span data-stu-id="63b94-108">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
-   <span data-ttu-id="63b94-109">Czy usługa jest webhosted, używa plik \*.svc.</span><span class="sxs-lookup"><span data-stu-id="63b94-109">If your service is webhosted, it uses an \*.svc file.</span></span> <span data-ttu-id="63b94-110">Otwórz plik svc i zmodyfikować nazwę usługi, jak wskazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="63b94-110">Open the svc file and modify the name of your service as indicated in the following example.</span></span> <span data-ttu-id="63b94-111">Ten krok nie jest konieczne własnym obsługiwanych aplikacji, ponieważ nie ma żadnego pliku svc.</span><span class="sxs-lookup"><span data-stu-id="63b94-111">This step is not necessary for self-hosted applications, as there is no svc file.</span></span>  
  
```  
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a><span data-ttu-id="63b94-112">Zmiana nazwy kontraktu usługi WCF</span><span class="sxs-lookup"><span data-stu-id="63b94-112">Renaming a WCF Service Contract</span></span>  
  
-   <span data-ttu-id="63b94-113">Wykonaj poniższe kroki, aby zmienić nazwę kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="63b94-113">Perform the following steps to rename the service contract,</span></span>  
  
-   <span data-ttu-id="63b94-114">Zmień nazwę kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="63b94-114">Change the name of the service contract.</span></span>  
  
-   <span data-ttu-id="63b94-115">W pliku konfiguracji usługi należy zmienić nazwę kontraktu usługi na nową nazwę, którą wybrano, jak wskazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="63b94-115">In the configuration file of the service, change the name of the service contract to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="63b94-116">Może to być plik konfiguracji pliku app.config lub web.config, w zależności od modelu hostingu.</span><span class="sxs-lookup"><span data-stu-id="63b94-116">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
