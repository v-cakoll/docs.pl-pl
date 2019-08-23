---
title: Przechowywanie wersji kontraktów danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- versioning [WCF], data contracts
- versioning [WCF]
- data contracts [WCF], versioning
ms.assetid: 4a0700cb-5f5f-4137-8705-3a3ecf06461f
ms.openlocfilehash: 309cd891fd2d764314060e49a401bd1d8f7b8d32
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963263"
---
# <a name="data-contract-versioning"></a>Przechowywanie wersji kontraktów danych
W miarę rozwoju aplikacji może być również konieczna zmiana kontraktów danych używanych przez usługi. W tym temacie wyjaśniono, jak wersje umów dotyczących danych. W tym temacie opisano mechanizmy obsługi wersji kontraktu danych. Aby zapoznać się z kompletnymi wskazówkami dotyczącymi wersji, zobacz [najlepsze rozwiązania: Przechowywanie wersji](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)kontraktu danych.  
  
## <a name="breaking-vs-nonbreaking-changes"></a>Przerwanie a Nieprzerwane zmiany  
 Zmiany w kontrakcie danych mogą być przerywane lub nieprzerwane. Po zmianie kontraktu danych w sposób nieprzerwany aplikacja używająca starszej wersji kontraktu może komunikować się z aplikacją przy użyciu nowszej wersji, a aplikacja korzystająca z nowszej wersji kontraktu może komunikować się z aplikacją przy użyciu starszej wersji. Z drugiej strony, nieprzerwana zmiana uniemożliwia komunikację w jednym lub obu kierunkach.  
  
 Wszelkie zmiany typu, który nie ma wpływu na sposób jego przesyłania i odbierania, nie są przerywane. Takie zmiany nie zmieniają kontraktu danych, tylko typ podstawowy. Na przykład można zmienić nazwę pola w sposób niepodzielony, jeśli następnie ustawisz <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> Właściwość <xref:System.Runtime.Serialization.DataMemberAttribute> na nazwę starszej wersji. Poniższy kod przedstawia wersję 1 kontraktu danych.  
  
 [!code-csharp[C_DataContractVersioning#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#1)]
 [!code-vb[C_DataContractVersioning#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#1)]  
  
 Poniższy kod przedstawia nieprzerwaną zmianę.  
  
 [!code-csharp[C_DataContractVersioning#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#2)]
 [!code-vb[C_DataContractVersioning#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#2)]  
  
 Niektóre zmiany modyfikują przesyłane dane, ale mogą lub nie mogą być przerywane. Następujące zmiany są zawsze przerywane:  
  
- Zmiana wartości <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>lubkontraktudanych. <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>  
  
- Zmiana kolejności elementów członkowskich danych przy użyciu <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> właściwości. <xref:System.Runtime.Serialization.DataMemberAttribute>  
  
- Zmiana nazwy elementu członkowskiego danych.  
  
- Zmiana kontraktu danych elementu członkowskiego danych. Na przykład zmiana typu elementu członkowskiego danych z liczby całkowitej na ciąg lub z typu z kontraktem danych o nazwie "Customer" na typ z kontraktem danych o nazwie "Person".  
  
 Możliwe są również następujące zmiany.  
  
## <a name="adding-and-removing-data-members"></a>Dodawanie i usuwanie elementów członkowskich danych  
 W większości przypadków dodanie lub usunięcie elementu członkowskiego danych nie jest istotną zmianą, chyba że wymagana jest ścisła ważność schematu (nowe wystąpienia są weryfikowane względem starego schematu).  
  
 Gdy typ z dodatkowym polem jest deserializowany do typu z brakującym polem, dodatkowe informacje są ignorowane. (Mogą być również przechowywane w celach okrężnych; Aby uzyskać więcej informacji, zobacz Kontrakty [danych zgodne z](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)przekazaniem).  
  
 Gdy typ z brakującym polem jest deserializowany do typu z dodatkowym polem, dodatkowe pole ma wartość domyślną, zazwyczaj zero lub `null`. (Wartość domyślna może zostać zmieniona. Aby uzyskać więcej informacji, zobacz [wywołania zwrotne serializacji](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)odpornej na wersje).  
  
 `CarV1` Na przykład można użyć klasy na kliencie `CarV2` i klasy w usłudze `CarV1` lub można użyć klasy w usłudze i `CarV2` klasie na kliencie.  
  
 [!code-csharp[C_DataContractVersioning#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#3)]
 [!code-vb[C_DataContractVersioning#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#3)]  
  
 Punkt końcowy w wersji 2 może pomyślnie wysyłać dane do punktu końcowego w wersji 1. Serializowanie wersji 2 `Car` kontraktu danych daje kod XML podobny do poniższego.  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
    <HorsePower>300</HorsePower>  
</Car>  
```  
  
 Aparat deserializacji w wersji 1 nie znalazł zgodnego elementu członkowskiego danych dla `HorsePower` tego pola i odrzuca te dane.  
  
 Ponadto punkt końcowy w wersji 1 może wysyłać dane do punktu końcowego w wersji 2. Serializowanie wersji 1 `Car` kontraktu danych daje kod XML podobny do poniższego.  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
</Car>  
```  
  
 Deserializator wersji 2 nie wie, do czego `HorsePower` służy pole, ponieważ nie ma żadnych pasujących danych w przychodzącym formacie XML. Zamiast tego pole jest ustawione na wartość domyślną 0.  
  
## <a name="required-data-members"></a>Wymagane składowe danych  
 Składowa danych może być oznaczona jako wymagana przez ustawienie <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> właściwości <xref:System.Runtime.Serialization.DataMemberAttribute> do `true`. Jeśli podczas deserializacji brakuje wymaganych danych, zostanie zgłoszony wyjątek zamiast ustawiania elementu członkowskiego danych do jego wartości domyślnej.  
  
 Dodawanie wymaganego elementu członkowskiego danych jest istotną zmianą. Oznacza to, że nowszy typ można nadal wysyłać do punktów końcowych ze starszym typem, ale nie w inny sposób. Usunięcie elementu członkowskiego danych, który został oznaczony jako wymagany w dowolnej starszej wersji, jest również istotną zmianą.  
  
 `false` `true` `false` Zmiana wartości `true` właściwości z na na nie jest przerywana, ale zmiana jej z na wartość może zostać przerwana, jeśli żadna wcześniejsza wersja tego typu nie ma podanego elementu członkowskiego danych. <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>  
  
> [!NOTE]
> `true`Mimo że <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> właściwość jest ustawiona na, dane przychodzące mogą mieć wartość null lub zero, a typ musi być przygotowany do obsługi tej możliwości. Nie należy używać <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> jako mechanizmu zabezpieczeń, aby chronić przed nieprawidłowymi danymi przychodzącymi.  
  
## <a name="omitted-default-values"></a>Pominięte wartości domyślne  
 Jest możliwe (choć niezalecane), aby ustawić `EmitDefaultValue` właściwość atrybutu DataMemberAttribute na `false`, zgodnie z opisem w wartościach [domyślnych elementu członkowskiego danych](../../../../docs/framework/wcf/feature-details/data-member-default-values.md). Jeśli to ustawienie ma `false`wartość, element członkowski danych nie zostanie wyemitowany, jeśli zostanie ustawiona na jego wartości domyślne (zazwyczaj wartość null lub zero). Jest to niezgodne z wymaganymi elementami członkowskimi danych w różnych wersjach na dwa sposoby:  
  
- Kontrakt danych z elementem członkowskim danych, który jest wymagany w jednej wersji, nie może odbierać wartości domyślnych (null lub zero) z innej wersji, w której element członkowski `EmitDefaultValue` danych ma `false`ustawioną wartość.  
  
- Wymagany element członkowski danych, który `EmitDefaultValue` ma `false` ustawioną wartość, nie może zostać użyty do serializacji jego wartości domyślnej (null lub zero), ale może otrzymać taką wartość przy deserializacji. Powoduje to utworzenie problemu okrężnego (dane mogą zostać odczytane, ale te same dane nie mogą być zapisywane). W związku z `IsRequired` tym `true` , jeśli `false` jest i `EmitDefaultValue` znajduje się w jednej wersji, ta sama kombinacja powinna mieć zastosowanie do wszystkich innych wersji, tak że żadna wersja kontraktu danych nie będzie mogła utworzyć wartości, która nie powoduje rundy.  
  
## <a name="schema-considerations"></a>Zagadnienia dotyczące schematu  
 Aby dowiedzieć się, jakie schematy są generowane dla typów kontraktu danych, zobacz temat [Informacje o schemacie kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 Schemat WCF dla typów kontraktu danych nie ma żadnych przepisów dotyczących przechowywania wersji. Oznacza to, że schemat wyeksportowany z określonej wersji typu zawiera tylko te składowe danych, które znajdują się w tej wersji. <xref:System.Runtime.Serialization.IExtensibleDataObject> Implementacja interfejsu nie powoduje zmiany schematu dla typu.  
  
 Elementy członkowskie danych są domyślnie eksportowane do schematu jako elementy opcjonalne. Oznacza to, `minOccurs` że wartość (atrybut XML) jest ustawiona na 0. Wymagane składowe danych zostały wyeksportowane z `minOccurs` ustawioną na 1.  
  
 Wiele zmian uważanych za nieprzerwanie jest w rzeczywistości przerywane, jeśli wymagane jest ścisłe przestrzeganie schematu. W poprzednim `CarV1` przykładzie wystąpienie z `CarV2` `Model` tylko elementem zostanie zweryfikowane względem schematu (które ma zarówno `Model` i `Horsepower`, ale oba są opcjonalne). Jednak odwrócenie nie jest prawdziwe: `CarV2` wystąpienie nie może sprawdzić poprawności `CarV1` względem schematu.  
  
 Dwukrotne wyzwolenie obejmuje również pewne dodatkowe zagadnienia. Aby uzyskać więcej informacji, zobacz sekcję "zagadnienia dotyczące schematu" w [umowach dotyczących danych przesyłanych dalej](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
### <a name="other-permitted-changes"></a>Inne dozwolone zmiany  
 <xref:System.Runtime.Serialization.IExtensibleDataObject> Implementacja interfejsu jest zmianą nierozdzielającą. Niemniej jednak pomoc techniczna przy użyciu rundy nie istnieje dla wersji typu przed wersją, w której <xref:System.Runtime.Serialization.IExtensibleDataObject> została zaimplementowana. Aby uzyskać więcej informacji, zobacz [Kontrakty danych zgodne z przekazywaniem dalej](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
## <a name="enumerations"></a>Wyliczenia  
 Dodawanie lub usuwanie elementu członkowskiego wyliczenia jest istotną zmianą. Zmiana nazwy elementu członkowskiego wyliczenia jest przerywana, chyba że jego nazwa kontraktu jest taka sama jak w starej wersji przy użyciu `EnumMemberAttribute` atrybutu. Aby uzyskać więcej informacji, zobacz [typy wyliczeniowe w kontraktach danych](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).  
  
## <a name="collections"></a>Kolekcje  
 Większość zmian kolekcji jest nieprzerwana, ponieważ większość typów kolekcji są zamienne ze sobą w modelu kontraktu danych. Jednak niestandardowa kolekcja jest dostosowywana lub na odwrót jest istotną zmianą. Ponadto zmiana ustawień dostosowywania kolekcji jest istotną zmianą. oznacza to, że zmiana nazwy kontraktu danych i przestrzeni nazw, powtarzająca się nazwa elementu, nazwa elementu klucza i nazwa elementu wartości. Aby uzyskać więcej informacji na temat dostosowywania kolekcji, zobacz [typy kolekcji w kontraktach danych](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md).  
Naturalnie zmiana kontraktu danych kolekcji (na przykład zmiana listy liczb całkowitych na listę ciągów) jest istotną zmianą.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>
- <xref:System.Runtime.Serialization.SerializationException>
- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- [Wywołania zwrotne serializacji z tolerancją dla wersji](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)
- [Najlepsze rozwiązania: Przechowywanie wersji kontraktu danych](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)
- [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Równoważność kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [Kontrakty danych zgodne z nowszymi wersjami](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)
