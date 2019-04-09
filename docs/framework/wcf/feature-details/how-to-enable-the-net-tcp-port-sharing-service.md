---
title: 'Instrukcje: włączanie usługi współużytkowania portów Net.TCP'
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 77d1d983da87b37c6267cc38a16db446782797f1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130653"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a><span data-ttu-id="5df10-102">Instrukcje: włączanie usługi współużytkowania portów Net.TCP</span><span class="sxs-lookup"><span data-stu-id="5df10-102">How to: Enable the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="5df10-103">Windows Communication Foundation (WCF) używa usługi Windows o nazwie usługi udostępniania portów Net.TCP, ułatwiające Udostępnianie portów TCP wiele procesów.</span><span class="sxs-lookup"><span data-stu-id="5df10-103">Windows Communication Foundation (WCF) uses a Windows service called the Net.TCP Port Sharing Service to facilitate the sharing of TCP ports across multiple processes.</span></span> <span data-ttu-id="5df10-104">Ta usługa jest instalowana jako część usługi WCF, ale usługa nie jest włączona domyślnie w celu zapewnienia bezpieczeństwa i dlatego musi być włączone ręcznie przed pierwszym użyciu.</span><span class="sxs-lookup"><span data-stu-id="5df10-104">This service is installed as part of WCF, but the service is not enabled by default as a security precaution and so must be manually enabled prior to first use.</span></span> <span data-ttu-id="5df10-105">W tym temacie opisano sposób konfigurowania sieci TCP usługi udostępniania portów za pomocą przystawki programu Microsoft Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="5df10-105">This topic describes how to configure the Net TCP Port Sharing Service using the Microsoft Management Console (MMC) snap-In.</span></span>  
  
 <span data-ttu-id="5df10-106">Po włączyć usługi udostępniania portów Net.TCP i uruchom ją ręcznie, zobacz [jak: Konfigurowanie usługi WCF na potrzeby współużytkowania portów użyj](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) informacji o sposobie konfigurowania usługi, aby używać tej usługi.</span><span class="sxs-lookup"><span data-stu-id="5df10-106">After you enable the Net.TCP Port Sharing Service and start it manually, see [How to: Configure a WCF Service to Use Port Sharing](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) for information about how to configure your service to use this service.</span></span>  
  
 <span data-ttu-id="5df10-107">Dla przykładu korzystającego z usługi współużytkowania portów net.tcp://, zobacz [przykładowe udostępniania portów Net.TCP](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).</span><span class="sxs-lookup"><span data-stu-id="5df10-107">For a sample that uses net.tcp:// port sharing, see the [Net.TCP Port Sharing Sample](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).</span></span>  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a><span data-ttu-id="5df10-108">Aby włączyć usługi udostępniania portów Net.TCP przy użyciu konsoli MMC</span><span class="sxs-lookup"><span data-stu-id="5df10-108">To enable the Net.TCP Port Sharing Service using MMC</span></span>  
  
1.  <span data-ttu-id="5df10-109">Z Start menu, otwórz konsolę zarządzania usługami, albo, otwierając okno wiersza polecenia i wpisując `services.msc` lub przez otwarcie wykonywania i wpisując `services.msc` w polu Otwórz.</span><span class="sxs-lookup"><span data-stu-id="5df10-109">From the Start menu, open the Services Management Console either by opening a Command Prompt window and typing `services.msc` or by opening Run and typing `services.msc` into the Open box.</span></span>  
  
2.  <span data-ttu-id="5df10-110">W **nazwa** kolumny na liście usług, kliknij prawym przyciskiem myszy **usługi udostępniania portów Net.Tcp**i wybierz **właściwości** z menu.</span><span class="sxs-lookup"><span data-stu-id="5df10-110">In the **Name** column of the list of services, right-click the **Net.Tcp Port Sharing Service**, and select **Properties** from the menu.</span></span>  
  
3.  <span data-ttu-id="5df10-111">Do włączenia ręcznym uruchomieniu usługi, w **właściwości** wybierz okno **ogólne** kartę i w **uruchamiana** wybierz ręcznego, a następnie kliknij przycisk **Zastosuj**.</span><span class="sxs-lookup"><span data-stu-id="5df10-111">To enable the manual start-up of the service, in the **Properties** window select the **General** tab, and in the **Startup type** box select Manual, and then click **Apply**.</span></span>  
  
4.  <span data-ttu-id="5df10-112">Aby uruchomić usługę, w obszarze stanu usługi, kliknij przycisk **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="5df10-112">To start the service,  in the Service status area, click the **Start** button.</span></span> <span data-ttu-id="5df10-113">Stan usługi powinien być teraz ustawiony na "Uruchomiono".</span><span class="sxs-lookup"><span data-stu-id="5df10-113">The service status should now display "Started".</span></span>  
  
5.  <span data-ttu-id="5df10-114">Aby powrócić do listy usług, kliknij przycisk **OK**i zamknąć okno konsoli MMC.</span><span class="sxs-lookup"><span data-stu-id="5df10-114">To return to the list of services, click the **OK**, and exit the MMC Console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5df10-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="5df10-115">Example</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5df10-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5df10-116">See also</span></span>

- [<span data-ttu-id="5df10-117">Współużytkowanie portów w składniku Net.TCP</span><span class="sxs-lookup"><span data-stu-id="5df10-117">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="5df10-118">Konfigurowanie usługi współużytkowania portów Net.TCP</span><span class="sxs-lookup"><span data-stu-id="5df10-118">Configuring the Net.TCP Port Sharing Service</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
