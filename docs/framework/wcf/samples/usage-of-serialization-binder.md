---
title: Używanie obiektu wiążącego serializacji
ms.date: 03/30/2017
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
ms.openlocfilehash: 10900950b935b484053fe8e37263f0dfc25eba99
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348455"
---
# <a name="usage-of-serialization-binder"></a><span data-ttu-id="6aaa5-102">Używanie obiektu wiążącego serializacji</span><span class="sxs-lookup"><span data-stu-id="6aaa5-102">Usage of Serialization Binder</span></span>
<span data-ttu-id="6aaa5-103">Ten przykład ilustruje sposób używania <xref:System.Runtime.Serialization.SerializationBinder> Aby zmienić wersję typu ogólnego, gdy jest serializowana.</span><span class="sxs-lookup"><span data-stu-id="6aaa5-103">This sample shows how to use the <xref:System.Runtime.Serialization.SerializationBinder> to change the version of a generic type when it is serialized.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="6aaa5-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="6aaa5-104">Demonstrates</span></span>  
 <span data-ttu-id="6aaa5-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span><span class="sxs-lookup"><span data-stu-id="6aaa5-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="6aaa5-106">Dyskusja</span><span class="sxs-lookup"><span data-stu-id="6aaa5-106">Discussion</span></span>  
 <span data-ttu-id="6aaa5-107">Niniejszy przykład pokazuje jak dwie jednostki, że są określania wartości docelowej różne wersje usługi .NET Framework mogą komunikować się za pomocą binarny program formatujący i integratora serializacji.</span><span class="sxs-lookup"><span data-stu-id="6aaa5-107">This sample shows how two entities that are targeting different versions of the .NET Framework can communicate using the binary formatter and the serialization binder.</span></span>  
  
<span data-ttu-id="6aaa5-108">W tym przykładzie został opracowany przy użyciu wywołaniem funkcji zdalnych .NET.</span><span class="sxs-lookup"><span data-stu-id="6aaa5-108">This sample was developed using .NET Remoting.</span></span> <span data-ttu-id="6aaa5-109">Składa się z serwerem określania wartości docelowej [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], który implementuje kontrakt typy ogólne i dwóch różnych klientów, co określania wartości docelowej platformy .NET Framework 2.0 i przeznaczone dla innej [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6aaa5-109">It consists of a server targeting [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], which implements a contract with generic types, and two different clients, one targeting .NET Framework 2.0 and another targeting [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].</span></span>  
  
 <span data-ttu-id="6aaa5-110">Dołącza serwera <xref:System.Runtime.Serialization.SerializationBinder> do binarny program formatujący, aby można było zmienić wersję typy odpowiednio na serializacji, więc obaj klienci może wykonywać deserializację tych typów prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="6aaa5-110">The server attaches a <xref:System.Runtime.Serialization.SerializationBinder> to the binary formatter to be able to change the version of the types accordingly on serialization, so both clients can deserialize those types properly.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6aaa5-111">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="6aaa5-111">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="6aaa5-112">Aby wykonać klienta, kliknij prawym przyciskiem myszy rozwiązanie, SBGenericsVTS (6 projekty), a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="6aaa5-112">To execute the client, right-click the solution, SBGenericsVTS (6 projects) and then select **Properties**.</span></span>  
  
2. <span data-ttu-id="6aaa5-113">W **wspólne właściwości**, wybierz opcję **projekt startowy**, a następnie wybierz **wiele projektów startowych**.</span><span class="sxs-lookup"><span data-stu-id="6aaa5-113">In **Common Properties**, select **Startup Project**, then select **Multiple Startup Projects**.</span></span>  
  
3. <span data-ttu-id="6aaa5-114">Wybierz **serwera** pierwszy, następnie **Client20** i następnie **Client40**.</span><span class="sxs-lookup"><span data-stu-id="6aaa5-114">Select **Server** first, then **Client20** and then **Client40**.</span></span> <span data-ttu-id="6aaa5-115">Wybierz **Start** działanie tych trzech projektów oraz pozostawienie pozostałych równa **Brak**.</span><span class="sxs-lookup"><span data-stu-id="6aaa5-115">Select the **Start** action to these three projects and leave the rest set to **None**.</span></span>  
  
4. <span data-ttu-id="6aaa5-116">Kliknij przycisk **OK** a następnie naciśnij klawisz F5, aby uruchomić próbki.</span><span class="sxs-lookup"><span data-stu-id="6aaa5-116">Click **OK** and then press F5 to run the sample.</span></span>
