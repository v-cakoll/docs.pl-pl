---
title: 'Model danych jednostki: Typy danych pierwotnych'
ms.date: 03/30/2017
ms.assetid: 7635168e-0566-4fdd-8391-7941b0d9f787
ms.openlocfilehash: 044a0ed981bb9cda3550fb3a3a9f1cb9bff96f25
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59142652"
---
# <a name="entity-data-model-primitive-data-types"></a>Model danych jednostki: Typy danych pierwotnych
Entity Data Model (EDM) obsługuje zestaw abstrakcyjne pierwotne typy danych (na przykład ciąg, wartość logiczna, Int32 i tak dalej), które są używane do definiowania [właściwości](../../../../docs/framework/data/adonet/property.md) w modelu koncepcyjnym. Te typy danych pierwotnych są serwery proxy dla rzeczywistego pierwotne typy danych, które są obsługiwane w magazynie, czy środowisko hostingu, takich jak bazy danych programu SQL Server lub środowisko uruchomieniowe języka wspólnego (CLR). EDM nie definiuje semantykę operacji lub przeliczeń za pośrednictwem pierwotne typy danych; Semantyka te są definiowane przez Magazyn lub środowisko hostingu. Zazwyczaj pierwotne typy danych w EDM są mapowane do odpowiedniego pierwotne typy danych w pamięci masowej lub środowisko hostingu. Aby dowiedzieć się, jak sposób Entity Framework mapowania typów pierwotnych w EDM do typów danych programu SQL Server, zobacz [SqlClient dla typów programu Entity Framework](../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).  
  
> [!NOTE]
>  Nie obsługuje kolekcji typów danych pierwotnych EDM.  
  
 Aby uzyskać informacji na temat typów danych strukturalnych EDM, zobacz [typu jednostki](../../../../docs/framework/data/adonet/entity-type.md) i [typu złożonego](../../../../docs/framework/data/adonet/complex-type.md).  
  
## <a name="primitive-data-types-supported-in-the-entity-data-model"></a>Typy pierwotne danych obsługiwane w modelu Entity Data Model  
 W poniższej tabeli przedstawiono typy pierwotne danych obsługiwane przez EDM. Podano również [aspektami](../../../../docs/framework/data/adonet/facet.md) , mogą być stosowane do poszczególnych typów danych pierwotnych.  
  
|Typem danych pierwotnych|Opis|Zastosowanie zestawów reguł|  
|-------------------------|-----------------|-----------------------|  
|plików binarnych|Zawiera dane binarne.|Element MaxLength, wartości null, domyślne|  
|Boolean|Zawiera wartość `true` lub `false`.|Wartość null, domyślne|  
|Byte|Zawiera wartość Liczba całkowita bez znaku 8-bitowych.|Precyzja dopuszczającego wartość null, domyślny|  
|DataGodzina|Reprezentuje datę i godzinę.|Precyzja dopuszczającego wartość null, domyślny|  
|DateTimeOffset|Zawiera datę i godzinę w ciągu kilku minut od GMT przesunięcia.|Precyzja dopuszczającego wartość null, domyślny|  
|Wartość dziesiętna|Zawiera wartość liczbową ze stałym dokładności i skali.|Precyzja dopuszczającego wartość null, domyślny|  
|Double|Zawiera zmiennoprzecinkowa numer z dokładnością do 15 cyfr.|Precyzja dopuszczającego wartość null, domyślny|  
|Float|Zawiera zmiennoprzecinkowa numer z siedmiu cyfr precyzji.|Precyzja dopuszczającego wartość null, domyślny|  
|Guid|Zawiera unikatowy identyfikator 16-bajtowy.|Precyzja dopuszczającego wartość null, domyślny|  
|Int16|Zawiera wartość liczby całkowitej ze znakiem 16-bitowych.|Precyzja dopuszczającego wartość null, domyślny|  
|Int32|Zawiera wartość całkowita 32-bitowa.|Precyzja dopuszczającego wartość null, domyślny|  
|Int64|Zawiera wartość całkowita 64-bitowa.|Precyzja dopuszczającego wartość null, domyślny|  
|SByte|Zawiera wartość całkowita 8-bitowa.|Precyzja dopuszczającego wartość null, domyślny|  
|String|Zawiera dane znaków.|Unicode dla wpisu, MaxLength, sortowanie, dokładności, dopuszczającego wartość null, domyślne|  
|Godzina|Zawiera porze dnia.|Precyzja dopuszczającego wartość null, domyślny|  
  
## <a name="see-also"></a>Zobacz także

- [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
