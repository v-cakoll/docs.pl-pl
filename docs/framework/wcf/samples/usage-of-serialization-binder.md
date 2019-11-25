---
title: Używanie obiektu wiążącego serializacji
ms.date: 03/30/2017
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
ms.openlocfilehash: bfce2a14c8757250c520919c8ff2a4d7048a9d5c
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74138646"
---
# <a name="usage-of-serialization-binder"></a><span data-ttu-id="7054e-102">Używanie obiektu wiążącego serializacji</span><span class="sxs-lookup"><span data-stu-id="7054e-102">Usage of Serialization Binder</span></span>
<span data-ttu-id="7054e-103">Ten przykład pokazuje, jak za pomocą <xref:System.Runtime.Serialization.SerializationBinder> zmienić wersję typu ogólnego podczas serializacji.</span><span class="sxs-lookup"><span data-stu-id="7054e-103">This sample shows how to use the <xref:System.Runtime.Serialization.SerializationBinder> to change the version of a generic type when it is serialized.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="7054e-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="7054e-104">Demonstrates</span></span>  
 <span data-ttu-id="7054e-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span><span class="sxs-lookup"><span data-stu-id="7054e-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="7054e-106">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="7054e-106">Discussion</span></span>  
 <span data-ttu-id="7054e-107">Ten przykład pokazuje, jak dwie jednostki, które są ukierunkowane na różne wersje .NET Framework mogą komunikować się przy użyciu binarnego programu formatującego i spinacza serializacji.</span><span class="sxs-lookup"><span data-stu-id="7054e-107">This sample shows how two entities that are targeting different versions of the .NET Framework can communicate using the binary formatter and the serialization binder.</span></span>  
  
<span data-ttu-id="7054e-108">Ten przykład został opracowany przy użyciu usług zdalnych platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="7054e-108">This sample was developed using .NET Remoting.</span></span> <span data-ttu-id="7054e-109">Składa się ona z serwera docelowego .NET Framework 4, który implementuje kontrakt z typami ogólnymi i dwóch różnych klientów, jeden element docelowy .NET Framework 2,0 i inny element docelowy .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7054e-109">It consists of a server targeting .NET Framework 4, which implements a contract with generic types, and two different clients, one targeting .NET Framework 2.0 and another targeting .NET Framework 4.</span></span>  
  
 <span data-ttu-id="7054e-110">Serwer dołącza <xref:System.Runtime.Serialization.SerializationBinder> do pliku binarnego programu formatującego, aby można było zmienić wersję typów odpowiednio dla serializacji, tak aby obaj klienci mogli prawidłowo deserializować te typy.</span><span class="sxs-lookup"><span data-stu-id="7054e-110">The server attaches a <xref:System.Runtime.Serialization.SerializationBinder> to the binary formatter to be able to change the version of the types accordingly on serialization, so both clients can deserialize those types properly.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7054e-111">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="7054e-111">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="7054e-112">Aby wykonać klienta, kliknij prawym przyciskiem myszy rozwiązanie, SBGenericsVTS (6 projektów), a następnie wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="7054e-112">To execute the client, right-click the solution, SBGenericsVTS (6 projects) and then select **Properties**.</span></span>  
  
2. <span data-ttu-id="7054e-113">W obszarze **wspólne właściwości**wybierz pozycję **projekt startowy**, a następnie wybierz opcję **wiele projektów startowych**.</span><span class="sxs-lookup"><span data-stu-id="7054e-113">In **Common Properties**, select **Startup Project**, then select **Multiple Startup Projects**.</span></span>  
  
3. <span data-ttu-id="7054e-114">Najpierw wybierz **serwer** , a następnie **Client20** , a następnie **Client40**.</span><span class="sxs-lookup"><span data-stu-id="7054e-114">Select **Server** first, then **Client20** and then **Client40**.</span></span> <span data-ttu-id="7054e-115">Wybierz akcję **Rozpocznij** dla tych trzech projektów i pozostaw wartość nie ustawiony na **none**.</span><span class="sxs-lookup"><span data-stu-id="7054e-115">Select the **Start** action to these three projects and leave the rest set to **None**.</span></span>  
  
4. <span data-ttu-id="7054e-116">Kliknij przycisk **OK** , a następnie naciśnij klawisz F5, aby uruchomić przykład.</span><span class="sxs-lookup"><span data-stu-id="7054e-116">Click **OK** and then press F5 to run the sample.</span></span>
