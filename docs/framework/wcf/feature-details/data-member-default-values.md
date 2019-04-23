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
ms.openlocfilehash: 2d323566aa211ced9ed76302756ed5dc82c5d2c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973723"
---
# <a name="data-member-default-values"></a>Domyślne wartości elementów członkowskich danych
W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], typy mają koncepcji *wartości domyślne*. Na przykład dla dowolnego typu odwołania, wartość domyślna to `null`, a typ liczby całkowitej wynosi zero. Należy co pewien czas pominięto element członkowski danych z serializowanych danych, gdy jest ustawiona na wartość domyślną. Ponieważ element członkowski ma wartość domyślną, wartość rzeczywistą nie muszą podlegać serializacji; ma to zalety wydajności.  
  
 Aby pominąć elementu członkowskiego w danych serializacji, należy ustawić <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> właściwość <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu `false` (wartość domyślna to `true`).  
  
> [!NOTE]
>  Należy ustawić <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> właściwości `false` w przypadku określonych trzeba to zrobić, takie jak współdziałanie lub danych rozmiar redukcji.  
  
## <a name="example"></a>Przykład  
 Poniższy kod zawiera kilka elementów członkowskich z <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> równa `false`.  
  
 [!code-csharp[DataMemberAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datamemberattribute/cs/overview.cs#4)]
 [!code-vb[DataMemberAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datamemberattribute/vb/overview.vb#4)]  
  
 Jeśli wystąpienie tej klasy jest serializowana, wynik jest następujący: `employeeName` i `employeeID` jest serializowana. Wartość null dla `employeeName` i wartości zero dla `employeeID` jest jawnie część serializowanych danych. Jednak `position`, `salary`, i `bonus` elementy członkowskie nie są serializowane. Na koniec `targetSalary` jest serializowany w zwykły sposób, nawet jeśli <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> właściwość jest ustawiona na `false`, ponieważ 57800 jest niezgodna z wartością domyślną .NET dla liczby całkowitej, która jest równa zero.  
  
### <a name="xml-representation"></a>Reprezentacja XML  
 Jeśli w poprzednim przykładzie, jest serializowany do XML, reprezentacja jest podobny do następującego.  
  
```xml  
<Employee>  
   <employeeName xsi:nil="true" />  
   <employeeID>0</employeeID>  
<targetSalary>57800</targetSalary>  
</Employee>  
```  
  
 `xsi:nil` Atrybut jest atrybutem specjalne w przestrzeni nazw wystąpienia schematu XML World Wide Web Consortium (W3C), który zapewnia sposób interoperacyjny jawnie reprezentujący wartość null. Należy pamiętać, że żadne informacje w ogóle w formacie XML o pozycja, wynagrodzenie i dodatkowe elementy członkowskie danych. Stronie odbierającej może interpretować je jako `null`, zerowego, i `null`, odpowiednio. Nie ma żadnej gwarancji, który Deserializator innych firm może zgłaszać poprawną interpretację, dlatego ten wzorzec nie jest zalecane. <xref:System.Runtime.Serialization.DataContractSerializer> Klasy zawsze wybiera poprawną interpretację dotyczącą brakujących wartości.  
  
### <a name="interaction-with-isrequired"></a>Interakcja z IsRequired  
 Zgodnie z opisem w [przechowywanie wersji kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md), <xref:System.Runtime.Serialization.DataMemberAttribute> atrybut ma <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> właściwość (wartość domyślna to `false`). Właściwość wskazuje, czy element członkowski danych danego musi znajdować się w serializowane dane, gdy jest on przeprowadzona. Jeśli `IsRequired` jest ustawiona na `true`, (wskazuje, że wartość musi być obecny) i <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> jest ustawiona na `false` (co oznacza, że wartość nie może być wyświetlany, jeśli jest ustawiona na wartość domyślną), wartości domyślne dla tego elementu członkowskiego danych nie może być. serializowany, ponieważ wyniki będą sprzeczne. Jeśli element członkowski danych jest ustawiony na wartość domyślną (zazwyczaj `null` lub zerem) i podejmowana jest próba serializacji, <xref:System.Runtime.Serialization.SerializationException> zgłaszany.  
  
### <a name="schema-representation"></a>Reprezentacja schematu  
 Szczegółowe informacje o reprezentacji schematu języka (XSD) definicji schematu XML składowych danych podczas `EmitDefaultValue` właściwość jest ustawiona na `false` zostały omówione w [odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Jednakże Oto krótki przegląd:  
  
-   Gdy <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> ustawiono `false`, jest reprezentowana w schemacie jako adnotacja określonych do programu Windows Communication Foundation (WCF). Nie ma interoperacyjne możliwości do reprezentowania tych informacji. W szczególności atrybutu "default" w schemacie nie jest używany w tym celu `minOccurs` atrybutu, dotyczy tylko przez <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> ustawienie i `nillable` atrybut dotyczy tylko typu składowej danych.  
  
-   Nie ma wartości rzeczywistych do użycia w schemacie. Jest odbieranie punkt końcowy, aby odpowiednio interpretacji brakującego elementu.  
  
 Podczas importowania schematu <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> zostaje automatycznie ustalona `false` zawsze, gdy adnotacji specyficzne dla usługi WCF wymienionych wcześniej wykrycia. Jest również ustawiona na `false` dla typów odwołań, które mają `nillable` właściwością `false` do obsługi scenariuszy określonych współdziałanie, często występujących podczas używania [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] usług sieci Web.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
