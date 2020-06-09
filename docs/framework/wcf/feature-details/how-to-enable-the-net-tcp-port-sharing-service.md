---
title: 'Instrukcje: Włączanie usługi współużytkowania portów Net.TCP'
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 8b305b98d620636328866bce848411f395053485
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593155"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a><span data-ttu-id="7af07-102">Instrukcje: Włączanie usługi współużytkowania portów Net.TCP</span><span class="sxs-lookup"><span data-stu-id="7af07-102">How to: Enable the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="7af07-103">Windows Communication Foundation (WCF) używa usługi systemu Windows o nazwie Usługa udostępniania portów Net. TCP w celu ułatwienia udostępniania portów TCP w wielu procesach.</span><span class="sxs-lookup"><span data-stu-id="7af07-103">Windows Communication Foundation (WCF) uses a Windows service called the Net.TCP Port Sharing Service to facilitate the sharing of TCP ports across multiple processes.</span></span> <span data-ttu-id="7af07-104">Ta usługa jest instalowana w ramach programu WCF, ale usługa nie jest domyślnie włączona z zabezpieczeniami i dlatego musi być włączona ręcznie przed pierwszym użyciem.</span><span class="sxs-lookup"><span data-stu-id="7af07-104">This service is installed as part of WCF, but the service is not enabled by default as a security precaution and so must be manually enabled prior to first use.</span></span> <span data-ttu-id="7af07-105">W tym temacie opisano sposób konfigurowania usługi udostępniania portów TCP sieci przy użyciu przystawki programu Microsoft Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="7af07-105">This topic describes how to configure the Net TCP Port Sharing Service using the Microsoft Management Console (MMC) snap-In.</span></span>  
  
 <span data-ttu-id="7af07-106">Po włączeniu usługi udostępniania portów Net. TCP i uruchomieniu jej ręcznie zapoznaj się z tematem [jak: Konfigurowanie usługi WCF do używania udostępniania portów](how-to-configure-a-wcf-service-to-use-port-sharing.md) , aby uzyskać informacje o sposobie konfigurowania usługi do korzystania z tej usługi.</span><span class="sxs-lookup"><span data-stu-id="7af07-106">After you enable the Net.TCP Port Sharing Service and start it manually, see [How to: Configure a WCF Service to Use Port Sharing](how-to-configure-a-wcf-service-to-use-port-sharing.md) for information about how to configure your service to use this service.</span></span>  
  
 <span data-ttu-id="7af07-107">Aby uzyskać przykład, który używa net. TCP://udostępniania portów, zobacz [przykład udostępniania portów Net. TCP](../samples/net-tcp-port-sharing-sample.md).</span><span class="sxs-lookup"><span data-stu-id="7af07-107">For a sample that uses net.tcp:// port sharing, see the [Net.TCP Port Sharing Sample](../samples/net-tcp-port-sharing-sample.md).</span></span>  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a><span data-ttu-id="7af07-108">Aby włączyć usługę udostępniania portów Net. TCP przy użyciu programu MMC</span><span class="sxs-lookup"><span data-stu-id="7af07-108">To enable the Net.TCP Port Sharing Service using MMC</span></span>  
  
1. <span data-ttu-id="7af07-109">Z menu Start Otwórz konsolę zarządzania usługami, otwierając okno wiersza polecenia i wpisując `services.msc` lub otwierając polecenie Uruchom i wpisując `services.msc` w polu Otwórz.</span><span class="sxs-lookup"><span data-stu-id="7af07-109">From the Start menu, open the Services Management Console either by opening a Command Prompt window and typing `services.msc` or by opening Run and typing `services.msc` into the Open box.</span></span>  
  
2. <span data-ttu-id="7af07-110">W kolumnie **Nazwa** listy usług kliknij prawym przyciskiem myszy **usługę udostępniania portów Net. TCP**, a następnie wybierz polecenie **Właściwości** z menu.</span><span class="sxs-lookup"><span data-stu-id="7af07-110">In the **Name** column of the list of services, right-click the **Net.Tcp Port Sharing Service**, and select **Properties** from the menu.</span></span>  
  
3. <span data-ttu-id="7af07-111">Aby włączyć ręczne uruchamianie usługi, w oknie **Właściwości** wybierz kartę **Ogólne** , a następnie w polu **Typ uruchomienia** wybierz pozycję ręcznie, a następnie kliknij pozycję **Zastosuj**.</span><span class="sxs-lookup"><span data-stu-id="7af07-111">To enable the manual start-up of the service, in the **Properties** window select the **General** tab, and in the **Startup type** box select Manual, and then click **Apply**.</span></span>  
  
4. <span data-ttu-id="7af07-112">Aby uruchomić usługę, w obszarze Stan usługi kliknij przycisk **Uruchom** .</span><span class="sxs-lookup"><span data-stu-id="7af07-112">To start the service,  in the Service status area, click the **Start** button.</span></span> <span data-ttu-id="7af07-113">Stan usługi powinien teraz zawierać wartość "uruchomiona".</span><span class="sxs-lookup"><span data-stu-id="7af07-113">The service status should now display "Started".</span></span>  
  
5. <span data-ttu-id="7af07-114">Aby powrócić do listy usług, kliknij przycisk **OK**i zamknij konsolę MMC.</span><span class="sxs-lookup"><span data-stu-id="7af07-114">To return to the list of services, click the **OK**, and exit the MMC Console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7af07-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="7af07-115">Example</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7af07-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7af07-116">See also</span></span>

- [<span data-ttu-id="7af07-117">Współużytkowanie portów w składniku Net.TCP</span><span class="sxs-lookup"><span data-stu-id="7af07-117">Net.TCP Port Sharing</span></span>](net-tcp-port-sharing.md)
- [<span data-ttu-id="7af07-118">Konfigurowanie usługi współużytkowania portów Net.TCP</span><span class="sxs-lookup"><span data-stu-id="7af07-118">Configuring the Net.TCP Port Sharing Service</span></span>](configuring-the-net-tcp-port-sharing-service.md)
