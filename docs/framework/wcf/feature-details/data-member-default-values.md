---
title: Domyślne wartości elementów członkowskich danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data members [WCF], default values
- data members [WCF]
ms.assetid: 53a3b505-4b27-444b-b079-0eb84a97cfd8
ms.openlocfilehash: 477921069411bb4b7ac32a5e93cc409bc7fbdec2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="data-member-default-values"></a>Domyślne wartości elementów członkowskich danych
W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], typy korzystają z pojęcia *wartości domyślne*. Na przykład dla dowolnego typu odwołania, wartością domyślną jest `null`, i dla typu Liczba całkowita jest równa 0. Jest czasami pożądane, aby pominąć elementu członkowskiego danych z danych serializacji, gdy jest ustawiona na wartość domyślną. Ponieważ element członkowski ma wartość domyślną, wartość rzeczywista nie wymagają serializacji; to ustawienie korzyści wydajności.  
  
 Aby pominąć element członkowski danych serializacji, ustaw <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> właściwość <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu `false` (wartość domyślna to `true`).  
  
> [!NOTE]
>  Należy ustawić <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> właściwości `false` gdy istnieje konkretna potrzeba Aby to zrobić, takie jak współdziałanie lub danych rozmiar odstępu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod zawiera kilka elementów członkowskich z <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> ustawioną `false`.  
  
 [!code-csharp[DataMemberAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datamemberattribute/cs/overview.cs#4)]
 [!code-vb[DataMemberAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datamemberattribute/vb/overview.vb#4)]  
  
 Jeśli wystąpienie tej klasy jest serializowana, wynik jest następujący: `employeeName` i `employeeID` jest serializowany. Wartość null dla `employeeName` i wartość zerową dla `employeeID` jest jawnie część danych serializacji. Jednak `position`, `salary`, i `bonus` elementy członkowskie nie są serializowane. Na koniec `targetSalary` jest serializowany w zwykły sposób, nawet jeśli <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> właściwość jest ustawiona na `false`, ponieważ 57800 jest niezgodna z wartością domyślną .NET dla całkowitą, która jest równa zero.  
  
### <a name="xml-representation"></a>Reprezentacja XML  
 Jeśli w poprzednim przykładzie jest serializowana do pliku XML, reprezentacja jest podobny do następującego.  
  
```xml  
<Employee>  
   <employeeName xsi:nil="true" />  
   <employeeID>0</employeeID>  
<targetSalary>57800</targetSalary>  
</Employee>  
```  
  
 `xsi:nil` Jest atrybutem specjalne w przestrzeni nazw schematu XML w sieci World Wide Web konsorcjum W3C wystąpienia, który zapewnia współdziałanie sposób jawnie reprezentowania wartości null. Należy pamiętać, że nie ma żadnych informacji w ogóle w kodzie XML o pozycji, wynagrodzenie i podwyższenie elementy członkowskie danych. Stronie odbierającej może interpretować je jako `null`, zero, i `null`odpowiednio. Nie ma żadnej gwarancji, który Deserializator innych firm może zgłaszać poprawnej interpretacji, dlatego ten wzorzec jest niezalecane. <xref:System.Runtime.Serialization.DataContractSerializer> Klasy zawsze wybiera poprawnej interpretacji dla brakujących wartości.  
  
### <a name="interaction-with-isrequired"></a>Interakcja z IsRequired  
 Zgodnie z opisem w [przechowywanie wersji kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md), <xref:System.Runtime.Serialization.DataMemberAttribute> ma atrybut <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> właściwość (wartość domyślna to `false`). Właściwość wskazuje, czy element członkowski danych danego musi znajdować się w danych serializacji. gdy jest poddawany deserializacji. Jeśli `IsRequired` ustawiono `true`, (co oznacza, że wartość musi być obecny) i <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> ma ustawioną wartość `false` (co oznacza, że wartość nie może być wyświetlany, jeśli jest ustawiona na wartość domyślną), nie może mieć wartości domyślne dla tego elementu członkowskiego danych serializowany, ponieważ wyniki będą sprzeczne. Jeśli element danych jest ustawiony na wartość domyślną (zazwyczaj `null` lub zerem) i serializacja zostanie podjęta, <xref:System.Runtime.Serialization.SerializationException> jest generowany.  
  
### <a name="schema-representation"></a>Reprezentacja schematu  
 Szczegóły schematu XML definition language (XSD) schematu reprezentacja elementy członkowskie danych podczas `EmitDefaultValue` właściwość jest ustawiona na `false` omówiono w [odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Jednak poniżej znajduje się krótki przegląd:  
  
-   Gdy <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> ma ustawioną wartość `false`, jest przedstawiany w schemacie adnotacji określonych do usługi Windows Communication Foundation (WCF). Nie istnieje sposób interoperacyjne do reprezentowania tych informacji. W szczególności atrybut "domyślny" w schemacie nie jest używany w tym celu `minOccurs` atrybut ma wpływ tylko przez <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> ustawienie i `nillable` atrybutu dotyczy tylko typu elementu członkowskiego danych.  
  
-   W schemacie nie ma wartości rzeczywistych do użycia. Jest odbierania punktu końcowego odpowiednio interpretować Brak elementu.  
  
 Podczas importowania schematu <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> jest automatycznie ustawiana właściwość `false` po każdej zmianie adnotacji specyficzne dla usługi WCF wymienione wcześniej została wykryta. Zostanie ona również ustawiona `false` dla typów odwołań, które mają `nillable` ustawioną właściwość `false` obsługi określonych współdziałanie, w których zwykle występują w przypadku uzyskiwania dostępu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] usług sieci Web.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>
