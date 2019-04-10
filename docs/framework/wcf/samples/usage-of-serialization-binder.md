---
title: Używanie obiektu wiążącego serializacji
ms.date: 03/30/2017
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
ms.openlocfilehash: 47a1974386927316ea9230ec27cf647d7245c44a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329846"
---
# <a name="usage-of-serialization-binder"></a><span data-ttu-id="0f25f-102">Używanie obiektu wiążącego serializacji</span><span class="sxs-lookup"><span data-stu-id="0f25f-102">Usage of Serialization Binder</span></span>
<span data-ttu-id="0f25f-103">Ten przykład ilustruje sposób używania <xref:System.Runtime.Serialization.SerializationBinder> Aby zmienić wersję typu ogólnego, gdy jest serializowana.</span><span class="sxs-lookup"><span data-stu-id="0f25f-103">This sample shows how to use the <xref:System.Runtime.Serialization.SerializationBinder> to change the version of a generic type when it is serialized.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="0f25f-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="0f25f-104">Demonstrates</span></span>  
 <xref:System.Runtime.Serialization.SerializationBinder><span data-ttu-id="0f25f-105">,</span><span class="sxs-lookup"><span data-stu-id="0f25f-105">,</span></span> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
  
## <a name="discussion"></a><span data-ttu-id="0f25f-106">Dyskusja</span><span class="sxs-lookup"><span data-stu-id="0f25f-106">Discussion</span></span>  
 <span data-ttu-id="0f25f-107">Ten przykład pokazuje, jak dwa jednostek, które są przeznaczone dla różnych wersji [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] może komunikować się przy użyciu binarny program formatujący i dla integratora serializacji.</span><span class="sxs-lookup"><span data-stu-id="0f25f-107">This sample shows how two entities that are targeting different versions of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] can communicate using the binary formatter and the serialization binder.</span></span>  
  
 <span data-ttu-id="0f25f-108">Rozwój w tym przykładzie zostały wykonane przy użyciu wywołaniem funkcji zdalnych .NET.</span><span class="sxs-lookup"><span data-stu-id="0f25f-108">The development of this sample has been done using .NET Remoting.</span></span> <span data-ttu-id="0f25f-109">Przykład składa się z serwerem określania wartości docelowej [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], który implementuje kontrakt typy ogólne i dwóch różnych klientów, jeden dla [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] i ustawianie elementów docelowych innej [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0f25f-109">The sample consists of a server targeting [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], which implements a contract with generic types, and two different clients, one targeting [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] and another targeting [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].</span></span>  
  
 <span data-ttu-id="0f25f-110">Dołącza serwera <xref:System.Runtime.Serialization.SerializationBinder> do binarny program formatujący, aby można było zmienić wersję typy odpowiednio na serializacji, więc obaj klienci może wykonywać deserializację tych typów prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="0f25f-110">The server attaches a <xref:System.Runtime.Serialization.SerializationBinder> to the binary formatter to be able to change the version of the types accordingly on serialization, so both clients can deserialize those types properly.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0f25f-111">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="0f25f-111">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="0f25f-112">Aby wykonać klienta, kliknij prawym przyciskiem myszy rozwiązanie, SBGenericsVTS (6 projekty), a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="0f25f-112">To execute the client, right-click the solution, SBGenericsVTS (6 projects) and then select **Properties**.</span></span>  
  
2. <span data-ttu-id="0f25f-113">W **wspólne właściwości**, wybierz opcję **projekt startowy**, a następnie wybierz **wiele projektów startowych**.</span><span class="sxs-lookup"><span data-stu-id="0f25f-113">In **Common Properties**, select **Startup Project**, then select **Multiple Startup Projects**.</span></span>  
  
3. <span data-ttu-id="0f25f-114">Wybierz **serwera** pierwszy, następnie **Client20** i następnie **Client40**.</span><span class="sxs-lookup"><span data-stu-id="0f25f-114">Select **Server** first, then **Client20** and then **Client40**.</span></span> <span data-ttu-id="0f25f-115">Wybierz **Start** działanie tych trzech projektów oraz pozostawienie pozostałych równa **Brak**.</span><span class="sxs-lookup"><span data-stu-id="0f25f-115">Select the **Start** action to these three projects and leave the rest set to **None**.</span></span>  
  
4. <span data-ttu-id="0f25f-116">Kliknij przycisk **OK** a następnie naciśnij klawisz F5, aby uruchomić próbki.</span><span class="sxs-lookup"><span data-stu-id="0f25f-116">Click **OK** and then press F5 to run the sample.</span></span>
