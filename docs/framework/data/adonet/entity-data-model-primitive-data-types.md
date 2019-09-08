---
title: 'Model danych jednostki: Typy danych pierwotnych'
ms.date: 03/30/2017
ms.assetid: 7635168e-0566-4fdd-8391-7941b0d9f787
ms.openlocfilehash: dd688a06a47f4c44c27ddee2120b9de6980672fc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795158"
---
# <a name="entity-data-model-primitive-data-types"></a>Model danych jednostki: Typy danych pierwotnych
Entity Data Model (EDM) obsługuje zestaw abstrakcyjnych typów danych pierwotnych (takich jak String, Boolean, Int32 itd.), które są używane do definiowania [Właściwości](property.md) w modelu koncepcyjnym. Te pierwotne typy danych to serwery proxy dla rzeczywistych typów danych pierwotnych, które są obsługiwane w środowisku magazynu lub hostingu, takie jak baza danych SQL Server lub środowisko uruchomieniowe języka wspólnego (CLR). Modelu EDM nie definiuje semantyki operacji lub konwersji w typach danych pierwotnych; Te semantyki są definiowane przez magazyn lub środowisko hostingu. Zazwyczaj typy danych pierwotnych w modelu EDM są mapowane na odpowiednie pierwotne typy danych w środowisku magazynu lub hostingu. Aby uzyskać informacje na temat sposobu, w jaki Entity Framework mapuje typy pierwotne w modelu EDM na SQL Server typów danych, zobacz [SqlClient for Entity Framework](./ef/sqlclient-for-ef-types.md).  
  
> [!NOTE]
> EDM nie obsługuje kolekcji typów danych pierwotnych.  
  
 Aby uzyskać informacje na temat typów danych strukturalnych w modelu EDM, zobacz [Typ jednostki](entity-type.md) i [typ złożony](complex-type.md).  
  
## <a name="primitive-data-types-supported-in-the-entity-data-model"></a>Typy danych pierwotnych obsługiwane w Entity Data Model  
 Poniższa tabela zawiera listę typów danych pierwotnych obsługiwanych przez modelu EDM. W tabeli wymieniono również zestawy [reguł](facet.md) , które mogą być stosowane do poszczególnych typów danych pierwotnych.  
  
|Typ danych pierwotnych|Opis|Odpowiednie aspekty|  
|-------------------------|-----------------|-----------------------|  
|plików binarnych|Zawiera dane binarne.|MaxLength, FixedLength, nullable, wartość domyślna|  
|Boolean|Zawiera wartość `true` lub `false`.|Dopuszcza wartość null, wartość domyślna|  
|Byte|Zawiera 8-bitową liczbę całkowitą bez znaku.|Precyzja, wartość null, wartość domyślna|  
|DataGodzina|Przedstawia datę i godzinę.|Precyzja, wartość null, wartość domyślna|  
|DateTimeOffset|Zawiera datę i godzinę przesunięcia w minutach od GMT.|Precyzja, wartość null, wartość domyślna|  
|Wartość dziesiętna|Zawiera wartość liczbową ze stałą dokładnością i skalą.|Precyzja, wartość null, wartość domyślna|  
|Double|Zawiera liczbę zmiennoprzecinkową z dokładnością do 15 cyfr.|Precyzja, wartość null, wartość domyślna|  
|Float|Zawiera liczbę zmiennoprzecinkową z dokładnością do siedmiu cyfr.|Precyzja, wartość null, wartość domyślna|  
|Guid|Zawiera unikatowy identyfikator 16-bajtowy.|Precyzja, wartość null, wartość domyślna|  
|Int16|Zawiera wartość 16-bitową liczbę całkowitą ze znakiem.|Precyzja, wartość null, wartość domyślna|  
|Int32|Zawiera podpisaną 32-bitową liczbę całkowitą.|Precyzja, wartość null, wartość domyślna|  
|Int64|Zawiera podpisaną 64-bitową liczbę całkowitą.|Precyzja, wartość null, wartość domyślna|  
|SByte|Zawiera 8-bitową liczbę całkowitą ze znakiem.|Precyzja, wartość null, wartość domyślna|  
|String|Zawiera dane znakowe.|Unicode, FixedLength, MaxLength, Collation, Precision, nullable, wartość domyślna|  
|Godzina|Zawiera godzinę.|Precyzja, wartość null, wartość domyślna|  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](entity-data-model-key-concepts.md)
- [Model danych jednostki](entity-data-model.md)
