---
title: Surogaty kontraktu danych
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], surrogates
ms.assetid: 8c31134c-46c5-4ed7-94af-bab0ac0dfce5
ms.openlocfilehash: cc0772cbb35f7c149af7eac04239d7349fa79f27
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797202"
---
# <a name="data-contract-surrogates"></a>Surogaty kontraktu danych
*Surogat* kontraktu danych to zaawansowana funkcja oparta na modelu kontraktu danych. Ta funkcja została zaprojektowana tak, aby była używana do dostosowywania typów i podstawiania w sytuacjach, gdy użytkownicy chcą zmienić sposób serializacji, deserializacji lub projekcji typu w metadanych. Niektóre scenariusze, w których można użyć surogatu, to w przypadku, gdy kontrakt danych nie został określony dla typu, pola i właściwości nie są oznaczone <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutem lub użytkownicy chcą dynamicznie tworzyć zmiany schematu.  
  
 Serializacja i deserializacja są realizowane przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer> surogatu kontraktu danych podczas konwertowania z .NET Framework do odpowiedniego formatu, takiego jak XML. Surogat kontraktu danych może również służyć do modyfikowania metadanych eksportowanych dla typów podczas tworzenia reprezentacji metadanych, takich jak dokumenty schematu XML (XSD). Po zaimportowaniu kod jest tworzony z metadanych, a Surogat może być używany w tym przypadku, aby dostosować wygenerowany kod.  
  
## <a name="how-the-surrogate-works"></a>Sposób działania surogatu  
 Surogat działa przez mapowanie jednego typu (typu "oryginalny") na inny typ (typ "Surogat"). W poniższym przykładzie przedstawiono oryginalny typ `Inventory` i nowy typ surogatu. `InventorySurrogated` Typ `Inventory` nie jest możliwy do serializacji, `InventorySurrogated` ale typ to:  
  
 [!code-csharp[C_IDataContractSurrogate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#1)]  
  
 Ponieważ nie zdefiniowano kontraktu danych dla tej klasy, przekonwertuj klasę na klasę zastępczą przy użyciu kontraktu danych. Klasa zastępcza jest pokazana w poniższym przykładzie:  
  
 [!code-csharp[C_IDataContractSurrogate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#2)]  
  
## <a name="implementing-the-idatacontractsurrogate"></a>Implementowanie IDataContractSurrogate  
 Aby użyć surogatu kontraktu danych, zaimplementuj <xref:System.Runtime.Serialization.IDataContractSurrogate> interfejs.  
  
 Poniżej przedstawiono omówienie każdej metody <xref:System.Runtime.Serialization.IDataContractSurrogate> z możliwością ewentualnej implementacji.  
  
### <a name="getdatacontracttype"></a>GetDataContractType  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> Metoda mapuje jeden typ na inny. Ta metoda jest wymagana do serializacji, deserializacji, importu i eksportu.  
  
 Pierwsze zadanie definiuje, jakie typy będą mapowane na inne typy. Na przykład:  
  
 [!code-csharp[C_IDataContractSurrogate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#3)]  
  
- W przypadku serializacji mapowanie zwrócone przez tę metodę jest następnie używane do przekształcania oryginalnego wystąpienia na wystąpienie zastępcze przez wywołanie <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> metody.  
  
- Podczas deserializacji mapowanie zwrócone przez tę metodę jest używane przez serializator do deserializacji w wystąpieniu typu surogatu. Następnie wywołuje <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> w celu przekształcenia zastępczego wystąpienia na wystąpienie oryginalnego typu.  
  
- W przypadku eksportu typ surogatu zwracany przez tę metodę jest odzwierciedlany w celu pobrania kontraktu danych do użycia w celu generowania metadanych.  
  
- Podczas importowania typ początkowy jest zmieniany na typ zastępczy, który jest odzwierciedlony w celu uzyskania kontraktu danych do celów, takich jak odwołująca się obsługa.  
  
 <xref:System.Type> Parametr jest typem obiektu, który jest serializowany, deserializowany, importowany lub eksportowany. <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> Metoda musi zwracać typ danych wejściowych, jeśli Surogat nie obsługuje tego typu. W przeciwnym razie Zwróć odpowiedni typ surogatu. Jeśli istnieje kilka typów surogatów, w tej metodzie można zdefiniować liczne mapowania.  
  
 Metoda nie jest wywoływana dla wbudowanych elementów podstawowych kontraktu danych, takich jak <xref:System.Int32> lub <xref:System.String>. <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> Dla innych typów, takich jak tablice, typy zdefiniowane przez użytkownika i inne struktury danych, ta metoda zostanie wywołana dla każdego typu.  
  
 W poprzednim przykładzie metoda sprawdza, czy `type` parametr i `Inventory` jest porównywalny. Jeśli tak, Metoda mapuje ją na `InventorySurrogated`. Za każdym razem, gdy jest wywoływana funkcja serializacji, deserializacji, schematu importu lub eksportu, jest wywoływana najpierw w celu określenia mapowania między typami.  
  
### <a name="getobjecttoserialize-method"></a>GetObjectToSerialize, Metoda  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> Metoda konwertuje oryginalne wystąpienie typu na wystąpienie typu z surogatem. Metoda jest wymagana do serializacji.  
  
 Następnym krokiem jest zdefiniowanie sposobu mapowania danych fizycznych z oryginalnego wystąpienia do surogatu przez implementację <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> metody. Na przykład:  
  
 [!code-csharp[C_IDataContractSurrogate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#4)]  
  
 Metoda <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> jest wywoływana, gdy obiekt jest serializowany. Ta metoda przenosi dane z oryginalnego typu do pól typu surogatu. Pola mogą być bezpośrednio mapowane na pola zastępcze lub manipulacje oryginalnymi danymi mogą być przechowywane w surogatie. Niektóre możliwe zastosowania obejmują: bezpośrednie Mapowanie pól, wykonywanie operacji na danych, które mają być przechowywane w polach zastępczych lub przechowywanie kodu XML oryginalnego typu w polu surogatu.  
  
 `targetType` Parametr odnosi się do zadeklarowanego typu elementu członkowskiego. Ten parametr jest typem surogatu zwracanym przez <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> metodę. Serializator nie wymusza, aby zwracany obiekt został przypisany do tego typu. `obj` Parametr jest obiektem do serializacji i zostanie przekonwertowany na jego Surogat, jeśli będzie to konieczne. Ta metoda musi zwracać obiekt wejściowy, jeśli Surogat nie obsłuży obiektu. W przeciwnym razie zostanie zwrócony nowy obiekt zastępczy. Surogat nie jest wywoływany, jeśli obiekt ma wartość null. W ramach tej metody można zdefiniować liczne mapowania zastępcze dla różnych wystąpień.  
  
 Podczas tworzenia <xref:System.Runtime.Serialization.DataContractSerializer>, możesz poinstruować, aby zachować odwołania do obiektów. (Aby uzyskać więcej informacji, zobacz [serializacji i deserializacji](../feature-details/serialization-and-deserialization.md)). W tym celu należy ustawić `preserveObjectReferences` parametr w konstruktorze na. `true` W takim przypadku Surogat jest wywoływany tylko raz dla obiektu, ponieważ wszystkie kolejne serializacji po prostu zapisują odwołanie do strumienia. Jeśli `preserveObjectReferences` jest ustawiona na `false`, Surogat jest wywoływana za każdym razem, gdy wystąpienie zostanie napotkane.  
  
 Jeśli typ serializowanego wystąpienia różni się od zadeklarowanego typu, informacje o typie są zapisywane w strumieniu, na przykład `xsi:type` w celu umożliwienia deserializacji wystąpienia na drugim końcu. Ten proces odbywa się niezależnie od tego, czy obiekt jest surogatem, czy nie.  
  
 Powyższy przykład konwertuje dane `Inventory` wystąpienia na `InventorySurrogated`wartość. Sprawdza typ obiektu i wykonuje wymagane manipulacje do konwersji na typ zastępczy. W takim przypadku pola `Inventory` klasy są kopiowane bezpośrednio `InventorySurrogated` do pól klas.  
  
### <a name="getdeserializedobject-method"></a>GetDeserializedObject, Metoda  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> Metoda konwertuje wystąpienie typu surogatu na wystąpienie pierwotne typu. Jest ona wymagana do deserializacji.  
  
 Następnym zadaniem jest zdefiniowanie sposobu mapowania danych fizycznych z wystąpienia surogatu do oryginału. Na przykład:  
  
 [!code-csharp[C_IDataContractSurrogate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#5)]  
  
 Ta metoda jest wywoływana tylko podczas deserializacji obiektu. Zapewnia odwrotne mapowanie danych dla deserializacji z typu surogatu z powrotem do jego oryginalnego typu. Podobnie jak metody, niektóre możliwe zastosowania mogą być bezpośrednio wymieniane danymi pól, wykonywać operacje na danych i przechowywać dane XML. `GetObjectToSerialize` Podczas deserializacji, użytkownik może nie zawsze uzyskać dokładne wartości danych ze ze względu na manipulacje w konwersji danych.  
  
 `targetType` Parametr odnosi się do zadeklarowanego typu elementu członkowskiego. Ten parametr jest typem surogatu zwracanym przez `GetDataContractType` metodę. `obj` Parametr odwołuje się do obiektu, który został deserializowany. Obiekt można przekonwertować z powrotem na jego oryginalny typ, jeśli jest on surogatem. Ta metoda zwraca obiekt wejściowy, jeśli Surogat nie obsłuży obiektu. W przeciwnym razie deserializowany obiekt zostanie zwrócony po zakończeniu konwersji. Jeśli istnieje kilka typów surogatów, można zapewnić konwersję danych z surogatu do typu podstawowego dla każdego z nich, wskazując każdy typ i jego konwersję.  
  
 Podczas zwracania obiektu wewnętrzne tabele obiektów są aktualizowane przy użyciu obiektu zwróconego przez ten Surogat. Wszystkie kolejne odwołania do wystąpienia uzyskają Surogat wystąpienia z tabel obiektów.  
  
 Poprzedni przykład konwertuje obiekty typu `InventorySurrogated` z powrotem do typu `Inventory`początkowego. W takim przypadku dane są przesyłane bezpośrednio z `InventorySurrogated` powrotem do odpowiednich pól w. `Inventory` Ze względu na to, że żadne operacje nie są manipulowane danymi, każde pole elementu członkowskiego będzie zawierać te same wartości jak przed serializacji.  
  
### <a name="getcustomdatatoexport-method"></a>GetCustomDataToExport Method  
 Podczas eksportowania schematu <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A> Metoda jest opcjonalna. Służy do wstawiania dodatkowych danych lub wskazówek do wyeksportowanego schematu. Dodatkowe dane można wstawiać na poziomie elementu członkowskiego lub na poziomie typu. Na przykład:  
  
 [!code-csharp[C_IDataContractSurrogate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#6)]  
  
 Ta metoda (z dwoma przeciążeniami) umożliwia dołączenie dodatkowych informacji do metadanych na poziomie elementu członkowskiego lub typu. Można uwzględnić wskazówki dotyczące tego, czy element członkowski jest publiczny, czy prywatny, oraz komentarze, które byłyby zachowane podczas eksportu i importu schematu. Takie informacje zostałyby utracone bez tej metody. Ta metoda nie powoduje wstawiania ani usuwania elementów członkowskich lub typów, ale raczej dodaje dodatkowe dane do schematów na dowolnym z tych poziomów.  
  
 Metoda jest przeciążona i może przyjmować `Type` albo (`clrtype` parametr), albo <xref:System.Reflection.MemberInfo> (`memberInfo` parametr). Drugi parametr jest zawsze `Type` (`dataContractType` parametr). Ta metoda jest wywoływana dla każdego elementu członkowskiego i typu klasy zastępczej `dataContractType` .  
  
 Jedno z tych przeciążeń musi `null` zwracać albo obiekt możliwy do serializacji. Obiekt o wartości innej niż null zostanie Zserializowany jako adnotacja do wyeksportowanego schematu. Dla przeciążenia każdy typ, który jest eksportowany do schematu jest wysyłany do tej metody w pierwszym parametrze wraz z typem surogatu `dataContractType` jako parametr. `Type` Dla przeciążenia każdy element członkowski wyeksportowany do schematu wysyła informacje `memberInfo` jako parametr z typem surogatu w drugim parametrze. `MemberInfo`  
  
#### <a name="getcustomdatatoexport-method-type-type"></a>GetCustomDataToExport — Metoda (typ, typ)  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Type%2CSystem.Type%29?displayProperty=nameWithType> Metoda jest wywoływana podczas eksportowania schematu dla każdej definicji typu. Metoda dodaje informacje do typów w schemacie podczas eksportowania. Każdy zdefiniowany typ jest wysyłany do tej metody w celu ustalenia, czy istnieją dodatkowe dane, które należy uwzględnić w schemacie.  
  
#### <a name="getcustomdatatoexport-method-memberinfo-type"></a>GetCustomDataToExport — Metoda (MemberInfo, typ)  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=nameWithType> Jest wywoływana podczas eksportowania dla każdego elementu członkowskiego w typach, które są eksportowane. Ta funkcja umożliwia dostosowanie wszelkich komentarzy do elementów członkowskich, które zostaną uwzględnione w schemacie podczas eksportowania. Informacje dla każdego elementu członkowskiego w klasie są wysyłane do tej metody, aby sprawdzić, czy w schemacie nie trzeba dodawać żadnych dodatkowych danych.  
  
 Powyższy przykład wyszukuje `dataContractType` dla każdego elementu członkowskiego surogatu. Następnie zwraca odpowiedni modyfikator dostępu dla każdego pola. Bez tego dostosowania wartość domyślna dla modyfikatorów dostępu jest publiczna. W związku z tym wszystkie elementy członkowskie byłyby zdefiniowane jako publiczne w kodzie wygenerowanym za pomocą wyeksportowanego schematu bez względu na to, jakie są ich rzeczywiste ograniczenia dostępu. Gdy ta implementacja nie jest używana, członek `numpens` będzie publiczny w wyeksportowanym schemacie, mimo że został zdefiniowany w surogatie jako prywatny. Za pomocą tej metody, modyfikator dostępu można wygenerować jako prywatny.  
  
### <a name="getreferencedtypeonimport-method"></a>GetReferencedTypeOnImport, Metoda  
 Ta metoda mapuje <xref:System.Type> Surogat na oryginalny typ. Ta metoda jest opcjonalna w przypadku zaimportowania schematu.  
  
 Podczas tworzenia surogatu, który importuje schemat i generuje dla niego kod, następnym zadaniem jest definiowanie typu wystąpienia surogatu do jego oryginalnego typu.  
  
 Jeśli wygenerowany kod musi odwoływać się do istniejącego typu użytkownika, odbywa się to przez implementację <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> metody.  
  
 Podczas importowania schematu ta metoda jest wywoływana dla każdej deklaracji typu w celu mapowania kontraktu danych zastępczych na typ. Parametry `typeName` ciągu i `typeNamespace` definiowania nazwy i przestrzeni nazw typu surogatu. Wartość zwracana przez <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> jest używana do określenia, czy należy wygenerować nowy typ. Ta metoda musi zwracać prawidłowy typ lub wartość null. W przypadku prawidłowych typów zwracany typ zostanie użyty jako przywoływany typ w wygenerowanym kodzie. Jeśli zwracana jest wartość null, nie będzie można odwoływać się do żadnego typu i należy utworzyć nowy typ. Jeśli istnieje kilka surogatów, możliwe jest przeprowadzenie mapowania dla każdego typu surogatu z powrotem do jego typu początkowego.  
  
 Parametr jest obiektem pierwotnie zwróconym przez <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A>. `customData` Ta `customData` funkcja jest używana, gdy autorzy zastępczi chcą wstawiać dodatkowe dane/wskazówki do metadanych do użycia podczas importowania w celu wygenerowania kodu.  
  
### <a name="processimportedtype-method"></a>ProcessImportedType, Metoda  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.ProcessImportedType%2A> Metoda dostosowuje wszystkie typy utworzone na podstawie importu schematu. Ta metoda jest opcjonalna.  
  
 Podczas importowania schematu ta metoda umożliwia dostosowanie wszelkich zaimportowanych typów i informacji o kompilacji. Przykład:  
  
 [!code-csharp[C_IDataContractSurrogate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#7)]  
  
 Podczas importowania ta metoda jest wywoływana dla każdego wygenerowanego typu. Zmień określony <xref:System.CodeDom.CodeTypeDeclaration> lub <xref:System.CodeDom.CodeCompileUnit>zmodyfikuj. Obejmuje to zmianę nazwy, członków, atrybutów i wielu innych właściwości `CodeTypeDeclaration`. Przetwarzając `CodeCompileUnit`, można modyfikować dyrektywy, przestrzenie nazw, zestawy, do których istnieją odwołania i kilka innych aspektów.  
  
 `CodeTypeDeclaration` Parametr zawiera deklarację typu kodu dom. `CodeCompileUnit` Parametr umożliwia modyfikację przetwarzania kodu.  Zwracanie `null` wyników w deklaracji typu odrzucone. Z drugiej strony, gdy `CodeTypeDeclaration`zwracają, modyfikacje są zachowywane.  
  
 Jeśli dane niestandardowe są wstawiane podczas eksportu metadanych, należy je dostarczyć użytkownikowi podczas importowania, aby można było go użyć. Te dane niestandardowe mogą służyć do programowania wskazówek dotyczących modelu lub innych komentarzy. Każdy `CodeTypeDeclaration` i <xref:System.CodeDom.CodeTypeMember> wystąpienie `IDataContractSurrogate` zawiera<xref:System.CodeDom.CodeObject.UserData%2A> dane niestandardowe jako właściwość, Rzutowanie na typ.  
  
 W powyższym przykładzie wykonywane są pewne zmiany w zaimportowanym schemacie. Kod zachowuje prywatne składowe oryginalnego typu za pomocą surogatu. Domyślny modyfikator dostępu podczas importowania schematu to `public`. W związku z tym wszystkie elementy członkowskie schematu zastępczego będą publiczne, chyba że zmodyfikowano, jak w tym przykładzie. Podczas eksportowania dane niestandardowe są wstawiane do metadanych, na których elementy członkowskie są prywatne. Przykład wyszukuje dane niestandardowe, sprawdza, czy modyfikator dostępu jest prywatny, a następnie modyfikuje odpowiedniego elementu członkowskiego, aby był prywatny przez ustawienie jego atrybutów. Bez tego dostosowania `numpens` członek zostanie zdefiniowany jako publiczny, a nie jako prywatny.  
  
### <a name="getknowncustomdatatypes-method"></a>GetKnownCustomDataTypes, Metoda  
 Ta metoda uzyskuje niestandardowe typy danych zdefiniowane ze schematu. Metoda jest opcjonalna dla importu schematu.  
  
 Metoda jest wywoływana na początku eksportowania schematu i importowania. Metoda zwraca niestandardowe typy danych używane w schemacie wyeksportowane lub zaimportowane. Metoda jest przenoszona a <xref:System.Collections.ObjectModel.Collection%601> `customDataTypes` (parametr), który jest kolekcją typów. Metoda powinna dodawać do tej kolekcji dodatkowe znane typy. Znane typy danych niestandardowych są konieczne, aby umożliwić serializacji i deserializacji danych niestandardowych przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer>. Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../feature-details/data-contract-known-types.md).  
  
## <a name="implementing-a-surrogate"></a>Implementacja surogatu  
 Aby użyć surogatu kontraktu danych w ramach programu WCF, należy wykonać kilka specjalnych procedur.  
  
### <a name="to-use-a-surrogate-for-serialization-and-deserialization"></a>Aby użyć surogatu do serializacji i deserializacji  
 <xref:System.Runtime.Serialization.DataContractSerializer> Użyj do wykonywania serializacji i deserializacji danych za pomocą surogatu. <xref:System.Runtime.Serialization.DataContractSerializer> Jest tworzony <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>przez. Należy również określić Surogat.  
  
##### <a name="to-implement-serialization-and-deserialization"></a>Aby zaimplementować serializacji i deserializacji  
  
1. Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> dla usługi. Aby uzyskać pełne instrukcje, zobacz [podstawowe programowanie WCF](../basic-wcf-programming.md).  
  
2. Dla każdego <xref:System.ServiceModel.Description.ServiceEndpoint> z określonych hostów usługi Znajdź jego <xref:System.ServiceModel.Description.OperationDescription>.  
  
3. Przeszukaj zachowania operacji, aby określić, czy znaleziono wystąpienie <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> .  
  
4. Jeśli zostanie znaleziona, ustaw jej <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> właściwość na nowe wystąpienie surogatu. <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> Jeśli nie <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> zostanie znaleziona, Utwórz nowe wystąpienie i <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> Ustaw element członkowski nowego zachowania na nowe wystąpienie surogatu.  
  
5. Na koniec Dodaj nowe zachowanie do bieżących zachowań operacji, jak pokazano w następującym przykładzie:  
  
     [!code-csharp[C_IDataContractSurrogate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#8)]  
  
### <a name="to-use-a-surrogate-for-metadata-import"></a>Aby użyć surogatu do importowania metadanych  
 Podczas importowania metadanych, takich jak WSDL i XSD, do generowania kodu po stronie klienta należy dodać Surogat do składnika odpowiedzialnego za generowanie kodu ze schematu <xref:System.Runtime.Serialization.XsdDataContractImporter>XSD. W tym celu należy bezpośrednio zmodyfikować <xref:System.ServiceModel.Description.WsdlImporter> użyte do zaimportowania metadanych.  
  
##### <a name="to-implement-a-surrogate-for-metadata-importation"></a>Aby zaimplementować Surogat dla transportu metadanych  
  
1. Zaimportuj metadane przy <xref:System.ServiceModel.Description.WsdlImporter> użyciu klasy.  
  
2. Użyj metody <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> , aby sprawdzić, <xref:System.Runtime.Serialization.XsdDataContractImporter> czy został zdefiniowany.  
  
3. `false` <xref:System.Runtime.Serialization.XsdDataContractImporter> Jeśli metoda zwraca, Utwórz nową i ustaw <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> <xref:System.Runtime.Serialization.ImportOptions> jej właściwość na nowe wystąpienie klasy. <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> W przeciwnym razie użyj importera zwróconego `out` przez parametr <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metody.  
  
4. Jeśli nie <xref:System.Runtime.Serialization.ImportOptions> zdefiniowano, ustaw właściwość jako nowe wystąpienie <xref:System.Runtime.Serialization.ImportOptions> klasy. <xref:System.Runtime.Serialization.XsdDataContractImporter>  
  
5. <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A> Ustaw właściwość <xref:System.Runtime.Serialization.ImportOptions> elementu nanowewystąpieniesurogatu.<xref:System.Runtime.Serialization.XsdDataContractImporter>  
  
6. Dodaj do kolekcji zwróconej <xref:System.ServiceModel.Description.MetadataExporter.State%2A> przez właściwość <xref:System.ServiceModel.Description.WsdlImporter> (Odziedziczone z <xref:System.ServiceModel.Description.MetadataExporter> klasy). <xref:System.Runtime.Serialization.XsdDataContractImporter>  
  
7. Użyj metody, <xref:System.ServiceModel.Description.WsdlImporter> aby zaimportować wszystkie Kontrakty danych w schemacie. <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> W ostatnim kroku kod jest generowany na podstawie schematów ładowanych przez wywołanie do surogatu.  
  
     [!code-csharp[C_IDataContractSurrogate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#9)]  
  
### <a name="to-use-a-surrogate-for-metadata-export"></a>Aby użyć surogatu do eksportu metadanych  
 Domyślnie podczas eksportowania metadanych z programu WCF dla usługi należy generować schemat WSDL i XSD. Surogat należy dodać do składnika odpowiedzialnego za generowanie schematu XSD dla typów <xref:System.Runtime.Serialization.XsdDataContractExporter>kontraktu danych. W tym celu należy użyć zachowania, które implementuje <xref:System.ServiceModel.Description.IWsdlExportExtension> <xref:System.ServiceModel.Description.WsdlExporter> <xref:System.ServiceModel.Description.WsdlExporter> , aby zmodyfikować lub bezpośrednio zmodyfikować używane do eksportowania metadanych.  
  
##### <a name="to-use-a-surrogate-for-metadata-export"></a>Aby użyć surogatu do eksportu metadanych  
  
1. Utwórz nowy <xref:System.ServiceModel.Description.WsdlExporter> lub `wsdlExporter` Użyj parametru przesłanego do <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> metody.  
  
2. Użyj funkcji <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> , aby sprawdzić, <xref:System.Runtime.Serialization.XsdDataContractExporter> czy został zdefiniowany.  
  
3. Jeśli <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> <xref:System.Runtime.Serialization.XsdDataContractExporter> zwraca <xref:System.ServiceModel.Description.WsdlExporter> <xref:System.ServiceModel.Description.MetadataExporter.State%2A> , Utwórz nowy z wygenerowanymi schematami XML z i <xref:System.ServiceModel.Description.WsdlExporter>Dodaj go do kolekcji zwróconej przez właściwość. `false` W przeciwnym razie użyj eksportu zwróconego przez `out` parametr <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metody.  
  
4. Jeśli nie <xref:System.Runtime.Serialization.ExportOptions>zdefiniowano , ustaw Właściwośćna<xref:System.Runtime.Serialization.ExportOptions> nowe wystąpienie klasy. <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> <xref:System.Runtime.Serialization.XsdDataContractExporter>  
  
5. <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A> Ustaw właściwość <xref:System.Runtime.Serialization.ExportOptions> elementu nanowewystąpieniesurogatu.<xref:System.Runtime.Serialization.XsdDataContractExporter> Kolejne kroki dotyczące eksportowania metadanych nie wymagają wprowadzania żadnych zmian.  
  
     [!code-csharp[C_IDataContractSurrogate#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#10)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.IDataContractSurrogate>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.Runtime.Serialization.ImportOptions>
- <xref:System.Runtime.Serialization.ExportOptions>
- [Używanie kontraktów danych](../feature-details/using-data-contracts.md)
