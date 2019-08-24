---
title: Kontrolowanie serializacji i deserializacji za pomocą elementu SerializationBinder
ms.date: 03/30/2017
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
ms.openlocfilehash: 29d48560cf25cd5c2e34d7a512d8c7079c65879e
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988217"
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a>Kontrolowanie serializacji i deserializacji za pomocą elementu SerializationBinder
Podczas serializacji, program formatujący przesyła informacje wymagane do utworzenia wystąpienia obiektu o poprawnym typie i wersji. Te informacje zazwyczaj obejmują pełną nazwę typu i nazwę zestawu obiektu. Domyślnie deserializacja używa tych informacji do utworzenia wystąpienia identycznego obiektu. Niektórzy użytkownicy mogą potrzebować kontroli klasy do serializacji i deserializacji, ponieważ oryginalna Klasa może nie istnieć na maszynie wykonującej deserializacji, Oryginalna klasa została przeniesiona między zestawami lub wymagana jest inna wersja klasy na serwer i klient. Aby uzyskać więcej informacji, zobacz [użycie spinacza serializacji](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).  
  
> [!WARNING]
> Ta funkcja jest dostępna tylko w przypadku korzystania <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> z programu <xref:System.Runtime.Serialization.NetDataContractSerializer>lub.  
  
## <a name="using-serializationbinder"></a>Korzystanie z pomocą elementu SerializationBinder  
 <xref:System.Runtime.Serialization.SerializationBinder>jest klasą abstrakcyjną służącą do kontrolowania rzeczywistych typów używanych podczas serializacji i deserializacji. Aby kontrolować typy używane podczas serializacji i deserializacji, należy utworzyć klasę z <xref:System.Runtime.Serialization.SerializationBinder> i <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> zastąpić metody i <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> . <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> Metoda<xref:System.Type> przyjmuje i zwraca zestaw i nazwę typu. Metoda przyjmuje zestaw i nazwę typu i <xref:System.Type>zwraca. <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)>  
  
## <a name="see-also"></a>Zobacz także

- [Serializacja i deserializacja](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)
- [Używanie obiektu wiążącego serializacji](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)
