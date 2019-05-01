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
ms.openlocfilehash: 53080975c03430a6c05bf72f58610b328430a3c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857158"
---
# <a name="data-contract-versioning"></a>Przechowywanie wersji kontraktów danych
W miarę ewolucji aplikacje, również może być konieczne zmiany danych umów dotyczących użycia usług. W tym temacie opisano sposób wersji kontraktów danych. W tym temacie opisano mechanizmy obsługi wersji kontraktu danych. Pełny przegląd i wskazówki wersji przetestowanego rozwiązania ze szczegółami, zobacz [najlepsze rozwiązania: Przechowywanie wersji kontraktów danych](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md).  
  
## <a name="breaking-vs-nonbreaking-changes"></a>Przerywanie programu vs. Zmiany nierozdzielający  
 Zmiany kontraktu danych można przerwanie lub nierozdzielające. Po zmianie w sposób nierozdzielający kontraktu danych aplikacji przy użyciu starszej wersji kontrakt może komunikować się z aplikacją przy użyciu nowszej wersji i aplikacji przy użyciu nowszej wersji kontrakt może komunikować się z aplikacją przy użyciu starszej wersji. Z drugiej strony istotną zmianę blokuje komunikację w jednym lub w obu kierunkach.  
  
 Wszelkie zmiany do typu, które nie wpływają na sposób jest wysłanych i odebranych są nieprzerywającymi działania aplikacji. Takie zmiany nie należy zmieniać kontraktu danych, typ podstawowy. Na przykład możesz można zmienić nazwę pola w taki sposób, nierozdzielający Jeśli następnie ustawisz <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> właściwość <xref:System.Runtime.Serialization.DataMemberAttribute> nazwę starszej wersji. Poniższy kod przedstawia wersję 1 kontraktu danych.  
  
 [!code-csharp[C_DataContractVersioning#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#1)]
 [!code-vb[C_DataContractVersioning#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#1)]  
  
 Poniższy kod pokazuje zmiany nieprzerywającymi działania aplikacji.  
  
 [!code-csharp[C_DataContractVersioning#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#2)]
 [!code-vb[C_DataContractVersioning#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#2)]  
  
 Niektóre zmiany modyfikują przesyłane dane, ale może lub nie mogą być istotne. Zawsze są istotne następujące zmiany:  
  
- Zmiana <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> lub <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> wartość kontraktu danych.  
  
- Zmiana kolejności elementów członkowskich danych za pomocą <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> właściwość <xref:System.Runtime.Serialization.DataMemberAttribute>.  
  
- Zmiana nazwy składowej danych.  
  
- Zmiana kontraktu danych składowej danych. Na przykład zmieniając typ element członkowski danych z liczbą całkowitą na ciąg lub typem za pomocą kontraktu danych o nazwie "Klient" do typu kontraktu danych o nazwie "Person".  
  
 Możliwe są również następujące zmiany.  
  
## <a name="adding-and-removing-data-members"></a>Dodawanie i usuwanie elementów członkowskich danych  
 W większości przypadków dodając lub usuwając element członkowski danych nie jest istotną zmianę, chyba że wymagają ważności ścisłego schematu (Sprawdzanie poprawności względem schematu stare nowych wystąpień).  
  
 Gdy typ o dodatkowe pola jest przeprowadzona na typ z brakujące pole, dodatkowe informacje są ignorowane. (Może to być również przechowywane w celach Pełna zgodnooć wersji; Aby uzyskać więcej informacji, zobacz [kontrakty danych zgodne](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)).  
  
 Gdy typ o brakujące pole jest przeprowadzona na typ o dodatkowe pola, dodatkowe pole pozostanie ustawiony na wartość domyślną, zwykle zero lub `null`. (Wartość domyślna może zostać zmieniona; Aby uzyskać więcej informacji, zobacz [wywołania zwrotne serializacji z tolerancją dla wersji](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md).)  
  
 Na przykład, można użyć `CarV1` klasy na komputerze klienckim i `CarV2` klasy na usługi lub mogą używać `CarV1` klasy usługi i `CarV2` klasy na komputerze klienckim.  
  
 [!code-csharp[C_DataContractVersioning#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#3)]
 [!code-vb[C_DataContractVersioning#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#3)]  
  
 Punkt końcowy w wersji 2 można pomyślnie wysyłać dane do punktu końcowego w wersji 1. Serializacji wersję 2 `Car` kontraktu danych daje XML, podobny do następującego.  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
    <HorsePower>300</HorsePower>  
</Car>  
```  
  
 Aparat deserializacji V1 nie znajdzie dopasowania element członkowski danych dla `HorsePower` pola i odrzuca te dane.  
  
 Ponadto punktu końcowego w wersji 1 umożliwia wysyłanie danych do punktu końcowego w wersji 2. Serializacji wersję 1 `Car` kontraktu danych daje XML, podobny do następującego.  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
</Car>  
```  
  
 Deserializator w wersji 2 nie wiedzieli, czego można ustawić `HorsePower` pola, ponieważ nie ma pasującego danych przychodzących pliku XML. Zamiast tego pola jest równa wartości domyślnej 0.  
  
## <a name="required-data-members"></a>Wymaganych składowych danych  
 Element członkowski danych może być oznaczony jako są wymagane przez ustawienie <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> właściwość <xref:System.Runtime.Serialization.DataMemberAttribute> do `true`. Jeśli jest to wymagane, że podczas deserializacji brakuje danych, wyjątek jest generowany zamiast ustawiać element członkowski danych do wartości domyślnej.  
  
 Dodawanie element członkowski danych wymagane jest zmianą przerywającą. Oznacza to nowszego typu mogą nadal być wysyłane do punktów końcowych przy użyciu starszych typu, ale nie odwrotnie. Usuwanie element członkowski danych, która została oznaczona jako wymagana w dowolnej wcześniejszej wersji jest również istotną zmianę.  
  
 Zmiana <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> wartość właściwości z `true` do `false` nie jest istotne, ale zmiana z `false` do `true` mogą być istotne, gdy wszystkie wcześniejsze wersje tego typu nie ma składowej danych, które w danym.  
  
> [!NOTE]
>  Mimo że <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> właściwość jest ustawiona na `true`, przychodzących danych może mieć wartości null lub zerową i typ musi być przygotowana do obsługi tej możliwości. Nie używaj <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> jako mechanizmu zabezpieczeń, aby zapewnić ochronę przed dane przychodzące są nieprawidłowe.  
  
## <a name="omitted-default-values"></a>Wartości domyślne pominięty  
 Jest możliwe (ale nie jest to zalecane) można ustawić `EmitDefaultValue` właściwości w atrybucie DataMemberAttribute na `false`, zgodnie z opisem w [domyślne wartości elementów członkowskich danych](../../../../docs/framework/wcf/feature-details/data-member-default-values.md). Jeśli to ustawienie jest `false`, składowa danych nie będzie emitowany, jeśli jest ustawiona na wartość domyślną (zazwyczaj wartość null lub zero). To nie jest zgodny z wymaganych składowych danych w różnych wersjach na dwa sposoby:  
  
- Kontrakt danych element członkowski danych, który jest wymagany w jednej wersji nie może odbierać domyślne (wartość null lub zero) danych z innej wersji, w którym element członkowski danych ma `EmitDefaultValue` równa `false`.  
  
- Element członkowski danych wymagane, który ma `EmitDefaultValue` równa `false` nie można używać do wykonywania serializacji domyślnej (wartość null lub zero) wartość, ale mogą odbierać wartość przy deserializacji. Spowoduje to utworzenie problemu Pełna zgodnooć wersji (dane mogą być odczytywane w, ale następnie nie może być zapisany tych samych danych). W związku z tym jeśli `IsRequired` jest `true` i `EmitDefaultValue` jest `false` w jednej wersji tej samej kombinacji stosuje się do wszystkich innych wersji taki sposób, że nie ma wersji kontraktu danych może wyprodukować wartość, która nie spowoduje komunikację dwustronną.  
  
## <a name="schema-considerations"></a>Zagadnienia dotyczące schematu  
 Objaśnienia dotyczące schematu, które są generowane dla typów kontraktu danych, zobacz [odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 Schemat WCF tworzy dla typy kontraktu danych sprawia, że nie postanowienia dotyczące wersji. Oznacza to, że schemat wyeksportowane z wersji typu zawiera tylko tych elementów członkowskich danych w tej wersji. Implementowanie <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejsu nie zmienia schemat dla typu.  
  
 Elementy członkowskie danych są eksportowane do schematu jako elementy opcjonalne, domyślnie. Oznacza to, że `minOccurs` (atrybut XML), wartość jest równa 0. Elementy członkowskie danych wymagane są eksportowane z `minOccurs` ustawiona na 1.  
  
 Wiele zmian uważane za nierozdzielających faktycznie są istotne, jeśli wymagana jest postępowania zgodnie ze schematem. W powyższym przykładzie `CarV1` wystąpienia z po prostu z `Model` elementu może przeprowadzić walidacji względem `CarV2` schematu (która ma zarówno `Model` i `Horsepower`, oba są opcjonalne, ale). Jednakże, odwrotna sytuacja nie jest wartość true: `CarV2` wystąpienia będą się kończyć niepowodzeniem weryfikacji względem `CarV1` schematu.  
  
 Pełna zgodnooć wersji także pociąga za sobą pewne dodatkowe zagadnienia. Aby uzyskać więcej informacji, zobacz sekcję "Uwagi dotyczące schematu" w [kontrakty danych zgodne](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
### <a name="other-permitted-changes"></a>Dozwolone inne zmiany  
 Implementowanie <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejsu według regionów powoduje zmianę nieprzerywającymi działania aplikacji. Jednak obsługa Pełna zgodnooć wersji nie istnieje dla wersji typu wcześniejszymi niż wersja, w którym <xref:System.Runtime.Serialization.IExtensibleDataObject> została zaimplementowana. Aby uzyskać więcej informacji, zobacz [kontrakty danych zgodne](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
## <a name="enumerations"></a>Wyliczenia  
 Dodawanie lub usuwanie elementu członkowskiego wyliczenia jest zmianą przerywającą. Zmiana nazwy elementu członkowskiego wyliczenia jest istotne, chyba że jego nazwa kontraktu jest taki sam jak stara wersja przechowywane przy użyciu `EnumMemberAttribute` atrybutu. Aby uzyskać więcej informacji, zobacz [Typy wyliczeniowe w kontraktach danych](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).  
  
## <a name="collections"></a>Kolekcje  
 Większość zmian kolekcji nieprzerywającymi działania aplikacji, ponieważ większość typów kolekcji czy zamienne ze sobą w modelu kontraktu danych. Jednak dokonywanie kolekcję noncustomized dostosowany lub odwrotnie jest zmianą przerywającą. Ponadto zmiana ustawień dostosowywania kolekcji jest zmianą przerywającą; oznacza to zmiana jego nazwy kontraktu danych i przestrzeni nazw, powtarzające się nazwy elementu, nazwa elementu klucza i wartości nazwy elementu. Aby uzyskać więcej informacji na temat dostosowywania kolekcji zobacz [typy kolekcji w kontraktach danych](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md).  
Oczywiście zmiana kontraktu danych treści kolekcji (np. zmiana na liście liczb całkowitych na listę ciągów) jest zmianą przerywającą.  
  
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
- [Najlepsze rozwiązania: Przechowywanie wersji kontraktów danych](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)
- [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Równoważność kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [Kontrakty danych zgodne z nowszymi wersjami](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)
