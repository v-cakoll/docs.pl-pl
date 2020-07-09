---
title: Zmienianie nazwy usługi WCF
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: 1179e7b235130e1967c79843b7a11f55622a01fb
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052055"
---
# <a name="renaming-a-wcf-service"></a><span data-ttu-id="04e50-102">Zmienianie nazwy usługi WCF</span><span class="sxs-lookup"><span data-stu-id="04e50-102">Renaming a WCF Service</span></span>
<span data-ttu-id="04e50-103">W tym temacie opisano, jak można zmienić nazwę usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="04e50-103">This topic describes how you can rename a Windows Communication Foundation (WCF) service.</span></span>  
  
## <a name="renaming-a-wcf-service"></a><span data-ttu-id="04e50-104">Zmienianie nazwy usługi WCF</span><span class="sxs-lookup"><span data-stu-id="04e50-104">Renaming a WCF Service</span></span>  
 <span data-ttu-id="04e50-105">Aby zmienić nazwę usługi w szablonie Windows Communication Foundation (WCF), wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="04e50-105">Perform the following steps to rename a service in a Windows Communication Foundation (WCF) template,</span></span>  
  
- <span data-ttu-id="04e50-106">Zmień nazwę klasy implementującej usługę.</span><span class="sxs-lookup"><span data-stu-id="04e50-106">Change the name of the class that implements the service.</span></span>  
  
- <span data-ttu-id="04e50-107">W pliku konfiguracji usługi Zmień nazwę usługi na nową wybraną nazwę, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="04e50-107">In the configuration file of the service, change the name of the service to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="04e50-108">Plik konfiguracji może być app.config lub web.config pliku w zależności od modelu hostingu.</span><span class="sxs-lookup"><span data-stu-id="04e50-108">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
- <span data-ttu-id="04e50-109">Jeśli usługa jest hostowana w sieci, używa pliku \* \* SVC\* .</span><span class="sxs-lookup"><span data-stu-id="04e50-109">If your service is webhosted, it uses an *\*.svc* file.</span></span> <span data-ttu-id="04e50-110">Otwórz plik SVC i zmodyfikuj nazwę usługi, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="04e50-110">Open the svc file and modify the name of your service as indicated in the following example.</span></span> <span data-ttu-id="04e50-111">Ten krok nie jest konieczny w przypadku aplikacji samodzielnych, ponieważ nie ma pliku SVC.</span><span class="sxs-lookup"><span data-stu-id="04e50-111">This step is not necessary for self-hosted applications, as there is no svc file.</span></span>  
  
```aspx-csharp
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a><span data-ttu-id="04e50-112">Zmiana nazwy kontraktu usługi WCF</span><span class="sxs-lookup"><span data-stu-id="04e50-112">Renaming a WCF Service Contract</span></span>  
  
- <span data-ttu-id="04e50-113">Aby zmienić nazwę kontraktu usługi, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="04e50-113">Perform the following steps to rename the service contract,</span></span>  
  
- <span data-ttu-id="04e50-114">Zmień nazwę kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="04e50-114">Change the name of the service contract.</span></span>  
  
- <span data-ttu-id="04e50-115">W pliku konfiguracji usługi Zmień nazwę kontraktu usługi na nową wybraną nazwę, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="04e50-115">In the configuration file of the service, change the name of the service contract to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="04e50-116">Plik konfiguracji może być app.config lub web.config pliku w zależności od modelu hostingu.</span><span class="sxs-lookup"><span data-stu-id="04e50-116">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
