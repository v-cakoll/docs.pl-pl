---
title: Przechowywanie wersji kontraktów danych
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- versioning [WCF], data contracts
- versioning [WCF]
- data contracts [WCF], versioning
ms.assetid: 4a0700cb-5f5f-4137-8705-3a3ecf06461f
caps.latest.revision: 35
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fd1679bb50a0dc6ee4997f7ae427c1cbdc0948ef
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="data-contract-versioning"></a>Przechowywanie wersji kontraktów danych
Jak aplikacje rozwijać, może również trzeba zmienić użycia usług kontraktów danych. W tym temacie opisano sposób wersji kontraktów danych. W tym temacie opisano mechanizmy kontroli wersji kontraktu danych. Pełny przegląd i wskazówki przetestowanego przechowywania wersji, zobacz [najlepsze rozwiązania: przechowywanie wersji kontraktów danych](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md).  
  
## <a name="breaking-vs-nonbreaking-changes"></a>Przerywanie vs. Zmiany nierozdzielający  
 Zmiany kontraktu danych można fundamentalne lub nierozdzielające. Po zmianie w sposób nierozdzielający kontraktu danych aplikacji przy użyciu starszej wersji produktu kontrakt może komunikować się z aplikacji przy użyciu nowszej wersji i aplikacji przy użyciu nowszej wersji kontraktu może komunikować się z aplikacją przy użyciu starszej wersji. Z drugiej strony na istotne zmiany blokuje komunikację w jednej lub obu kierunkach.  
  
 Wszelkie zmiany do typu, które nie mają wpływu na sposób jest wysłanych i odebranych zostają nierozdzielający. Takie zmiany nie należy zmieniać kontraktu danych, typ podstawowy. Na przykład można zmienić nazwę pola w sposób nierozdzielający Jeśli ustawisz następnie <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> właściwość <xref:System.Runtime.Serialization.DataMemberAttribute> do nazwy starszej wersji. Poniższy kod przedstawia wersji 1 kontraktu danych.  
  
 [!code-csharp[C_DataContractVersioning#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#1)]
 [!code-vb[C_DataContractVersioning#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#1)]  
  
 Poniższy kod przedstawia nierozdzielający zmiany.  
  
 [!code-csharp[C_DataContractVersioning#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#2)]
 [!code-vb[C_DataContractVersioning#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#2)]  
  
 Niektóre zmiany zmodyfikować przesyłane dane, ale może lub nie może być przerwanie. Zawsze pozbyciu się następujące zmiany:  
  
-   Zmiana <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> lub <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> wartość kontraktu danych.  
  
-   Zmiana kolejności elementów członkowskich danych przy użyciu <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> właściwość <xref:System.Runtime.Serialization.DataMemberAttribute>.  
  
-   Zmiana nazwy elementu członkowskiego danych.  
  
-   Zmiana kontraktu danych elementu członkowskiego danych. Na przykład zmiana typu elementu członkowskiego danych z liczbą całkowitą z ciągiem lub typem z kontrakt danych o nazwie "Klient" do typu z kontrakt danych o nazwie "Osoba".  
  
 Możliwe są następujące zmiany.  
  
## <a name="adding-and-removing-data-members"></a>Dodawanie i usuwanie elementów członkowskich danych  
 W większości przypadków Dodawanie lub usuwanie elementu członkowskiego danych nie jest istotne zmiany, chyba że wymagają ważności strict schematu (Sprawdzanie poprawności względem schematu starego nowych wystąpień).  
  
 Gdy typem z dodatkowe pola jest przeprowadzona deserializacja typu brakuje pola, dodatkowe informacje są ignorowane. (Może to być również przechowywane w celach dwustronną komunikację; Aby uzyskać więcej informacji, zobacz [kontrakty danych zgodne z nowszymi](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)).  
  
 Gdy typem z brakujące pole jest przeprowadzona deserializacja typu dodatkowe pola, dodatkowe pola pozostanie ustawiony na wartość domyślną, zwykle zero lub `null`. (Wartość domyślna mogą zostać zmienione; aby uzyskać więcej informacji, zobacz [wywołania zwrotne serializacji z tolerancją dla wersji](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md).)  
  
 Na przykład można użyć `CarV1` klasy na kliencie i `CarV2` klasy usługi, lub można użyć `CarV1` klasy usługi i `CarV2` klasy na kliencie.  
  
 [!code-csharp[C_DataContractVersioning#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#3)]
 [!code-vb[C_DataContractVersioning#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#3)]  
  
 Punkt końcowy w wersji 2 może pomyślnie wysyłać dane do punktu końcowego w wersji 1. Serializacji wersja 2 `Car` kontraktu danych daje XML podobny do następującego.  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
    <HorsePower>300</HorsePower>  
</Car>  
```  
  
 Aparat deserializacji na V1 nie znajdzie zgodnego elementu członkowskiego danych dla `HorsePower` pola i usuwanie tych danych.  
  
 Ponadto punkt końcowy w wersji 1 może wysyłać dane do punktu końcowego w wersji 2. Serializacji wersja 1 `Car` kontraktu danych daje XML podobny do następującego.  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
</Car>  
```  
  
 Deserializator w wersji 2 nie wiadomo co można ustawić `HorsePower` pola, ponieważ nie ma pasującego danych przychodzące dane XML. Zamiast tego pola ma ustawioną wartość domyślna 0.  
  
## <a name="required-data-members"></a>Wymaganych elementów członkowskich danych  
 Element członkowski danych mogą być oznaczone jako wymaganych przez ustawienie <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> właściwość <xref:System.Runtime.Serialization.DataMemberAttribute> do `true`. Jeśli jest to wymagane, że brakuje danych podczas deserializacji, jest zwracany wyjątek zamiast ustawiania elementu danych do wartości domyślnej.  
  
 Dodawanie elementu członkowskiego danych wymagane jest istotne zmiany. Oznacza to nowszego typu może nadal być wysyłane do punktów końcowych starsze typu, ale nie odwrotnie. Usuwanie elementu członkowskiego danych, który został oznaczony jako w wszelkie wcześniejsze niż wersja wymagana jest również istotne zmiany.  
  
 Zmiana <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> wartość właściwości z `true` do `false` nie przerywając, ale zmiana z `false` do `true` może być krytyczne, gdy wszystkie jego wcześniejsze wersje tego typu nie ma elementu członkowskiego danych zagrożona.  
  
> [!NOTE]
>  Mimo że <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> właściwość jest ustawiona na `true`, przychodzących danych może mieć wartości null lub zero, a typem muszą być przygotowane do obsługi tej możliwości. Nie używaj <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> jako mechanizm zabezpieczeń, aby zapewnić ochronę przed złe dane przychodzące.  
  
## <a name="omitted-default-values"></a>Wartości domyślne pominięty  
 Istnieje możliwość (chociaż nie jest to zalecane) można ustawić `EmitDefaultValue` właściwości w atrybucie DataMemberAttribute do `false`, zgodnie z opisem w [wartości domyślny element członkowski danych](../../../../docs/framework/wcf/feature-details/data-member-default-values.md). Jeśli to ustawienie jest `false`, element członkowski danych nie będzie emitowany, jeśli jest ustawiona na wartość domyślną (zazwyczaj wartość null lub zero). To nie jest zgodny z wymaganych elementów członkowskich danych w różnych wersjach na dwa sposoby:  
  
-   Kontrakt danych jest wymagany w jednej wersji elementu członkowskiego danych nie może odebrać domyślne (wartość null lub zero) danych w innej wersji, w którym ma element członkowski danych `EmitDefaultValue` ustawioną `false`.  
  
-   Wymagane dane elementu członkowskiego, który ma `EmitDefaultValue` ustawioną `false` nie można serializować domyślnej (wartość null lub zero), wartość, ale mogą odbierać wartość przy deserializacji. Powoduje to problem dwustronną komunikację (dane mogą być odczytywane w, ale następnie nie mogą być zapisywane tych samych danych). W związku z tym jeśli `IsRequired` jest `true` i `EmitDefaultValue` jest `false` w jednej wersji samej kombinacji powinno być stosowane do wszystkich innych wersji taki sposób, że nie ma wersji kontraktu danych można utworzyć wartość, która nie powoduje podróż.  
  
## <a name="schema-considerations"></a>Zagadnienia dotyczące schematu  
 Aby uzyskać informacje o jakie schematu jest generowany na typy kontraktu danych, zobacz [odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 Schemat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] na typy kontraktu danych i tworzy sprawia, że nie przepisy dotyczące przechowywania wersji. Oznacza to, że schemat wyeksportowane z wersji typu zawiera tylko te elementy członkowskie danych dostępne w tej wersji. Implementowanie <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejsu nie zmienia schemat dla typu.  
  
 Elementy członkowskie danych są eksportowane do schematu jako opcjonalne elementy domyślnie. Oznacza to `minOccurs` (atrybut XML) wartość jest równa 0. Elementy członkowskie danych wymagane są eksportowane z `minOccurs` ustawioną wartość 1.  
  
 Wiele zmian uważane za nierozdzielających są faktycznie krytyczne, jeśli wymagana jest ścisłego przestrzegania schematu. W powyższym przykładzie `CarV1` wystąpienia z tylko `Model` element czy sprawdzania poprawności `CarV2` schematu (który ma zarówno atrybut `Model` i `Horsepower`, oba warunki są opcjonalne, ale). Jednak odwrotnej nie jest prawdziwe: `CarV2` wystąpienia spowoduje niepowodzenie weryfikacji względem `CarV1` schematu.  
  
 Dwustronną komunikację wymaga także pewne dodatkowe kwestie. Aby uzyskać więcej informacji, zobacz sekcję "Zagadnienia dotyczące schematu" w [kontrakty danych zgodne z nowszymi](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
### <a name="other-permitted-changes"></a>Inne dozwolone zmiany  
 Implementowanie <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejs jest nierozdzielający zmiany. Jednak obsługa dwustronną komunikację nie istnieje dla wersje poprzedzające wersję, w którym typ <xref:System.Runtime.Serialization.IExtensibleDataObject> została zaimplementowana. Aby uzyskać więcej informacji, zobacz [kontrakty danych zgodne z nowszymi](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
## <a name="enumerations"></a>Wyliczenia  
 Dodawanie lub usuwanie elementu członkowskiego wyliczenia jest istotne zmiany. Zmiana nazwy elementu członkowskiego wyliczenia jest krytyczne, chyba że jego nazwa kontraktu pozostaje taki sam jak stara wersja przy użyciu `EnumMemberAtttribute` atrybutu. Aby uzyskać więcej informacji, zobacz [Typy wyliczeniowe w kontraktach danych](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).  
  
## <a name="collections"></a>Kolekcje  
 Większość zmian w kolekcji są nierozdzielający ponieważ większość typów kolekcji są wymienne ze sobą w modelu kontraktu danych. Jednak dokonywanie noncustomized kolekcji dostosowane lub odwrotnie jest istotne zmiany. Zmiana ustawień dostosowania kolekcji jest również istotne zmiany; oznacza to, że zmiana jego nazwie kontraktu danych i przestrzeni nazw, powtarzające się nazwy elementu, nazwa elementu klucza i wartość nazwy elementu. Aby uzyskać więcej informacji dotyczących dostosowywania kolekcji, zobacz [typy kolekcji w kontraktach danych](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md).  
Oczywiście zmiana z kontraktem danych zawartość kolekcji (np. zmiana z listy liczb całkowitych na listę ciągów) jest istotne zmiany.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>  
 <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>  
 <xref:System.Runtime.Serialization.SerializationException>  
 <xref:System.Runtime.Serialization.IExtensibleDataObject>  
 [Wywołania zwrotne serializacji z tolerancją dla wersji](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)  
 [Najlepsze rozwiązania: przechowywanie wersji kontraktów danych](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)  
 [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Równoważność kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [Kontrakty danych zgodne z nowszymi wersjami](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)
