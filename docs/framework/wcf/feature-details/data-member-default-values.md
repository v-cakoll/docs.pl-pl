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
ms.openlocfilehash: e4eaaec880ecfcff24d9d5b4e8347a84738e070b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593485"
---
# <a name="data-member-default-values"></a>Domyślne wartości elementów członkowskich danych
W .NET Framework typy mają koncepcję *wartości domyślnych*. Na przykład dla dowolnego typu odwołania wartość domyślna to `null` , a dla typu Integer jest równa zero. Czasami pożądane jest pominięcie elementu członkowskiego danych z serializowanych danych, gdy jest ustawiony na jego wartość domyślną. Ponieważ element członkowski ma wartość domyślną, nie trzeba serializować wartości rzeczywistej; jest to zalety wydajności.  
  
 Aby pominąć element członkowski z serializowanych danych, należy ustawić <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> Właściwość <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu na `false` (wartość domyślna to `true` ).  
  
> [!NOTE]
> Należy ustawić <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> Właściwość na `false` , jeśli istnieje taka konieczność, na przykład w przypadku współdziałania lub zmniejszania rozmiaru danych.  
  
## <a name="example"></a>Przykład  
 Poniższy kod ma kilku członków z <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> zestawem `false` .  
  
 [!code-csharp[DataMemberAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datamemberattribute/cs/overview.cs#4)]
 [!code-vb[DataMemberAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datamemberattribute/vb/overview.vb#4)]  
  
 Jeśli wystąpienie tej klasy jest serializowane, wynik jest następujący: `employeeName` i `employeeID` jest serializowany. Wartość null dla `employeeName` i wartość zerowa dla `employeeID` jest jawnie częścią serializowanych danych. Jednak `position` `salary` `bonus` elementy członkowskie, i nie są serializowane. Na koniec, `targetSalary` jest serializowany w zwykły sposób, mimo że <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> Właściwość jest ustawiona na `false` , ponieważ 57800 nie jest zgodna z wartością domyślną .NET dla liczby całkowitej, która jest równa zero.  
  
### <a name="xml-representation"></a>Reprezentacja XML  
 Jeśli poprzedni przykład jest serializowany do kodu XML, reprezentacja jest podobna do poniższego.  
  
```xml  
<Employee>  
   <employeeName xsi:nil="true" />  
   <employeeID>0</employeeID>  
<targetSalary>57800</targetSalary>  
</Employee>  
```  
  
 Ten `xsi:nil` atrybut jest atrybutem specjalnym w przestrzeni nazw wystąpienia schematu XML organizacja World Wide Web Consortium (W3C), który zapewnia interoperacyjny sposób jawnego reprezentowania wartości null. Zwróć uwagę, że w kodzie XML nie ma żadnych informacji o pozycji, wynagrodzeniu i elementach członkowskich danych. Na końcu można interpretować te `null` wartości, odpowiednio, zero i `null` . Nie ma gwarancji, że Deserializator innej firmy może wprowadzić poprawną interpretację, co oznacza, że ten wzorzec nie jest zalecany. <xref:System.Runtime.Serialization.DataContractSerializer>Klasa zawsze wybiera poprawną interpretację dla brakujących wartości.  
  
### <a name="interaction-with-isrequired"></a>Interakcja z IsRequired  
 Zgodnie z opisem w sekcji [przechowywanie wersji kontraktu danych](data-contract-versioning.md) <xref:System.Runtime.Serialization.DataMemberAttribute> atrybut ma <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> Właściwość (wartość domyślna to `false` ). Właściwość wskazuje, czy dany element członkowski danych musi znajdować się w serializowanych danych podczas deserializacji. Jeśli `IsRequired` jest ustawiona na `true` , (która wskazuje, że wartość musi być obecna) i <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> jest ustawiona na `false` (wskazując, że wartość nie może być obecna, jeśli jest ustawiona na wartość domyślną), wartości domyślne dla tego elementu członkowskiego danych nie mogą być serializowane, ponieważ wyniki byłyby sprzeczne. Jeśli taki element członkowski danych ma ustawioną wartość domyślną (zazwyczaj `null` lub zero) i podjęto próbę serializacji, <xref:System.Runtime.Serialization.SerializationException> jest zgłaszany.  
  
### <a name="schema-representation"></a>Reprezentacja schematu  
 Szczegóły schematu języka definicji schematu XML (XSD), gdy `EmitDefaultValue` Właściwość jest ustawiona na `false` jest omówiona w [odwołaniu do schematu kontraktu danych](data-contract-schema-reference.md). Poniżej przedstawiono jednak krótkie omówienie:  
  
- Gdy <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> jest ustawiona na `false` , jest reprezentowana w schemacie jako adnotacja specyficzna dla Windows Communication Foundation (WCF). Nie istnieje interoperacyjny sposób reprezentowania tych informacji. W szczególności atrybut "default" w schemacie nie jest używany do tego celu, `minOccurs` atrybut ma wpływ tylko na <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> ustawienie, a `nillable` atrybut ma wpływ tylko na typ elementu członkowskiego danych.  
  
- Rzeczywista wartość domyślna do użycia nie występuje w schemacie. Jest on do punktu końcowego odbioru w celu odpowiedniego zinterpretowania brakującego elementu.  
  
 W przypadku importowania schematu <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> Właściwość jest automatycznie ustawiana na `false` zawsze, gdy zostanie wykryta adnotacja specyficzna dla WCF. Jest on również ustawiony na `false` dla typów referencyjnych, które mają `nillable` ustawioną właściwość na `false` obsługę określonych scenariuszy współdziałania, które często występują podczas zużywania usług sieci Web ASP.NET.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
