---
title: 'Instrukcje: Włączanie usługi współużytkowania portów Net.TCP'
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 4b5a18e11d9fc15f23b5353883a63d838face58a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490763"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a><span data-ttu-id="a8b68-102">Instrukcje: Włączanie usługi współużytkowania portów Net.TCP</span><span class="sxs-lookup"><span data-stu-id="a8b68-102">How to: Enable the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="a8b68-103">Windows Communication Foundation (WCF) używa usługi systemu Windows o nazwie usługi udostępniania portów Net.TCP ułatwia udostępnianie portów TCP wielu procesom.</span><span class="sxs-lookup"><span data-stu-id="a8b68-103">Windows Communication Foundation (WCF) uses a Windows service called the Net.TCP Port Sharing Service to facilitate the sharing of TCP ports across multiple processes.</span></span> <span data-ttu-id="a8b68-104">Ta usługa jest instalowana jako część usługi WCF, ale usługa nie jest włączona domyślnie w celu zapewnienia bezpieczeństwa i dlatego muszą być włączone ręcznie przed pierwszym użyciem.</span><span class="sxs-lookup"><span data-stu-id="a8b68-104">This service is installed as part of WCF, but the service is not enabled by default as a security precaution and so must be manually enabled prior to first use.</span></span> <span data-ttu-id="a8b68-105">W tym temacie opisano sposób konfigurowania sieci TCP Port do udostępniania usługi za pomocą przystawki Microsoft Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="a8b68-105">This topic describes how to configure the Net TCP Port Sharing Service using the Microsoft Management Console (MMC) snap-In.</span></span>  
  
 <span data-ttu-id="a8b68-106">Po włączyć usługi udostępniania portów Net.TCP i uruchomić go ręcznie, zobacz [porady: Konfigurowanie usługi WCF na potrzeby współużytkowania portów użyj](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) informacji o sposobie konfigurowania usługi do tej usługi.</span><span class="sxs-lookup"><span data-stu-id="a8b68-106">After you enable the Net.TCP Port Sharing Service and start it manually, see [How to: Configure a WCF Service to Use Port Sharing](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) for information about how to configure your service to use this service.</span></span>  
  
 <span data-ttu-id="a8b68-107">Dla przykładu korzystającego z Udostępnianie portów net.tcp://, zobacz [przykład współużytkowania portów Net.TCP](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).</span><span class="sxs-lookup"><span data-stu-id="a8b68-107">For a sample that uses net.tcp:// port sharing, see the [Net.TCP Port Sharing Sample](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).</span></span>  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a><span data-ttu-id="a8b68-108">Aby włączyć usługi udostępniania portów Net.TCP przy użyciu konsoli MMC</span><span class="sxs-lookup"><span data-stu-id="a8b68-108">To enable the Net.TCP Port Sharing Service using MMC</span></span>  
  
1.  <span data-ttu-id="a8b68-109">Z Start menu, otwórz konsolę zarządzania usług albo otwierając okno wiersza polecenia i wpisując `services.msc` lub przez otwarcie Uruchom i wprowadzając polecenie `services.msc` w polu Otwórz.</span><span class="sxs-lookup"><span data-stu-id="a8b68-109">From the Start menu, open the Services Management Console either by opening a Command Prompt window and typing `services.msc` or by opening Run and typing `services.msc` into the Open box.</span></span>  
  
2.  <span data-ttu-id="a8b68-110">W **nazwa** kolumny na liście usług, kliknij prawym przyciskiem myszy **usługi udostępniania portów Net.Tcp**i wybierz **właściwości** z menu.</span><span class="sxs-lookup"><span data-stu-id="a8b68-110">In the **Name** column of the list of services, right-click the **Net.Tcp Port Sharing Service**, and select **Properties** from the menu.</span></span>  
  
3.  <span data-ttu-id="a8b68-111">Aby włączyć ręcznego uruchamiania usługi, w **właściwości** wybierz okno **ogólne** kartę i w **typ uruchamiania** wybierz ręcznego, a następnie kliknij przycisk **Zastosuj**.</span><span class="sxs-lookup"><span data-stu-id="a8b68-111">To enable the manual start-up of the service, in the **Properties** window select the **General** tab, and in the **Startup type** box select Manual, and then click **Apply**.</span></span>  
  
4.  <span data-ttu-id="a8b68-112">Aby uruchomić usługę, w obszarze stanu usługi, kliknij przycisk **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="a8b68-112">To start the service,  in the Service status area, click the **Start** button.</span></span> <span data-ttu-id="a8b68-113">Stan usługi powinien być teraz wyświetlany "Started".</span><span class="sxs-lookup"><span data-stu-id="a8b68-113">The service status should now display "Started".</span></span>  
  
5.  <span data-ttu-id="a8b68-114">Aby powrócić do listy usług, kliknij przycisk **OK**i zamknij konsolę MMC.</span><span class="sxs-lookup"><span data-stu-id="a8b68-114">To return to the list of services, click the **OK**, and exit the MMC Console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8b68-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="a8b68-115">Example</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8b68-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a8b68-116">See Also</span></span>  
 [<span data-ttu-id="a8b68-117">Współużytkowanie portów w składniku Net.TCP</span><span class="sxs-lookup"><span data-stu-id="a8b68-117">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 [<span data-ttu-id="a8b68-118">Konfigurowanie usługi współużytkowania portów Net.TCP</span><span class="sxs-lookup"><span data-stu-id="a8b68-118">Configuring the Net.TCP Port Sharing Service</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
