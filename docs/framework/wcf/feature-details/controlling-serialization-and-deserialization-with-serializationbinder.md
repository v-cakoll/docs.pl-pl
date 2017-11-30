---
title: "Kontrolowanie serializacji i deserializacji za pomocą elementu SerializationBinder"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: be5faf5e465eeacc190081c22d7bc59c3caf5825
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2017
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a><span data-ttu-id="06fb0-102">Kontrolowanie serializacji i deserializacji za pomocą elementu SerializationBinder</span><span class="sxs-lookup"><span data-stu-id="06fb0-102">Controlling Serialization and Deserialization with SerializationBinder</span></span>
<span data-ttu-id="06fb0-103">Podczas serializacji element formatujący przesyła informacje wymagane do utworzenia wystąpienia obiektu poprawnego typu i wersji.</span><span class="sxs-lookup"><span data-stu-id="06fb0-103">During serialization, a formatter transmits the information required to create an instance of an object of the correct type and version.</span></span> <span data-ttu-id="06fb0-104">Informacje te obejmują zazwyczaj Pełna nazwa typu i nazwy zestawu obiektu.</span><span class="sxs-lookup"><span data-stu-id="06fb0-104">This information generally includes the full type name and assembly name of the object.</span></span> <span data-ttu-id="06fb0-105">Domyślnie deserializacji używa tych informacji do utworzenia wystąpienia obiektu identyczne.</span><span class="sxs-lookup"><span data-stu-id="06fb0-105">By default, deserialization uses this information to create an instance of an identical object.</span></span> <span data-ttu-id="06fb0-106">W przypadku niektórych użytkowników może być konieczne do kontrolowania, która klasa w celu serializacji i deserializacji, albo ponieważ oryginalnej klasy mogą nie istnieć na komputerze wykonywania deserializacji, między zestawami przeniósł oryginalnej klasy lub inna wersja tej klasy jest wymagany na serwera i klienta.</span><span class="sxs-lookup"><span data-stu-id="06fb0-106">Some users may need to control which class to serialize and deserialize, either because the original class may not exist on the machine performing deserialization, the original class has moved between assemblies, or a different version of the class is required on the server and client.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="06fb0-107">[Używanie obiektu wiążącego serializacji](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).</span><span class="sxs-lookup"><span data-stu-id="06fb0-107"> [Usage of Serialization Binder](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="06fb0-108">Ta funkcja jest dostępna tylko w przypadku korzystania z <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> lub <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="06fb0-108">This functionality is only available when using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> or the <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span>  
  
## <a name="using-serializationbinder"></a><span data-ttu-id="06fb0-109">Za pomocą elementu SerializationBinder</span><span class="sxs-lookup"><span data-stu-id="06fb0-109">Using SerializationBinder</span></span>  
 <span data-ttu-id="06fb0-110"><xref:System.Runtime.Serialization.SerializationBinder>Klasa abstrakcyjna służy do kontroli rzeczywiste typy używane podczas serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="06fb0-110"><xref:System.Runtime.Serialization.SerializationBinder> is an abstract class used to control the actual types used during serialization and deserialization.</span></span> <span data-ttu-id="06fb0-111">Aby kontrolować typów używany podczas serializacji i deserializacji, klasa wyprowadzona z <xref:System.Runtime.Serialization.SerializationBinder> i zastąpić <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> i <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> metody.</span><span class="sxs-lookup"><span data-stu-id="06fb0-111">To control the types used during serialization and deserialization, derive a class from <xref:System.Runtime.Serialization.SerializationBinder> and override the <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> and <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> methods.</span></span> <span data-ttu-id="06fb0-112"><xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> Ma metody <xref:System.Type> i zwraca nazwę zestawu i typu.</span><span class="sxs-lookup"><span data-stu-id="06fb0-112">The <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> method takes a <xref:System.Type> and returns an assembly and type name.</span></span> <span data-ttu-id="06fb0-113"><xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> Metoda przyjmuje nazwę zestawu i typu i zwraca <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="06fb0-113">The <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> method takes an assembly and type name and returns a <xref:System.Type>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06fb0-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="06fb0-114">See Also</span></span>  
 [<span data-ttu-id="06fb0-115">Serializacja i deserializacja</span><span class="sxs-lookup"><span data-stu-id="06fb0-115">Serialization and Deserialization</span></span>](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)  
 [<span data-ttu-id="06fb0-116">Używanie obiektu wiążącego serializacji</span><span class="sxs-lookup"><span data-stu-id="06fb0-116">Usage of Serialization Binder</span></span>](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)
