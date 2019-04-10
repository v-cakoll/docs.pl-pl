---
title: Surogaty kontraktu danych
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], surrogates
ms.assetid: 8c31134c-46c5-4ed7-94af-bab0ac0dfce5
ms.openlocfilehash: f97826cb5154035b535b5eac3a8818d8b366d639
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59315351"
---
# <a name="data-contract-surrogates"></a>Surogaty kontraktu danych
Kontrakt danych *zastępczy* jest funkcją zaawansowaną utworzonych na podstawie modelu kontraktu danych. Ta funkcja jest przeznaczony do zastosowania w przypadku dostosowywania typu i podstawienia w sytuacjach, w którym użytkownicy chcą zmienić, jak typ jest serializowana, zdeserializowany lub przewidywanych do metadanych. Sytuacje, gdzie mogą być używane zastępczy jest, gdy kontrakt danych nie została określona dla typu, pola i właściwości nie są oznaczone za pomocą <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu lub użytkownicy chcą dynamiczne tworzenie odmiany schematu.  
  
 Serializacja i deserializacja są realizowane przy użyciu zastępczy kontraktu danych, korzystając z <xref:System.Runtime.Serialization.DataContractSerializer> można przekonwertować z .NET Framework na odpowiedni format, takich jak XML. Zastępczy kontraktu danych może również służyć do modyfikowania metadane wyeksportowane w przypadku typów podczas produkowania reprezentacje metadanych, takich jak dokumenty schematu XML (XSD). Po zaimportowaniu kod jest tworzona na podstawie metadanych i surogatu można w tym przypadku dostosować także wygenerowanego kodu.  
  
## <a name="how-the-surrogate-works"></a>Jak działa surogatu  
 Zastępczy działa przez mapowanie jeden typ ("oryginalne", typ) do innego typu (typu "surrogated"). W poniższym przykładzie pokazano oryginalny typ `Inventory` i nowe zastępczy `InventorySurrogated` typu. `Inventory` Typ nie jest możliwy do serializacji, ale `InventorySurrogated` typ to:  
  
 [!code-csharp[C_IDataContractSurrogate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#1)]  
  
 Ponieważ nie zdefiniowano kontraktu danych dla tej klasy, należy przekonwertować klasy do klasy zastępcze z kontraktu danych. W poniższym przykładzie pokazano surrogated klasy:  
  
 [!code-csharp[C_IDataContractSurrogate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#2)]  
  
## <a name="implementing-the-idatacontractsurrogate"></a>Implementowanie IDataContractSurrogate  
 Aby korzystać z surogatu kontraktu danych, należy zaimplementować <xref:System.Runtime.Serialization.IDataContractSurrogate> interfejsu.  
  
 Poniżej przedstawiono omówienie każdej metodzie <xref:System.Runtime.Serialization.IDataContractSurrogate> z możliwą implementację.  
  
### <a name="getdatacontracttype"></a>GetDataContractType  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> Metoda mapuje jednego typu na inny. Ta metoda jest wymagany do serializacji, deserializacji, importowanie i eksportowanie.  
  
 Pierwsze zadanie jest zdefiniowanie, jakie typy będą mapowane na inne typy. Na przykład:  
  
 [!code-csharp[C_IDataContractSurrogate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#3)]  
  
-   Na serializacji, mapowanie zwracanego przez tę metodę jest następnie używana do przekształcania oryginalnego wystąpienia surrogated wystąpienia przez wywołanie metody <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> metody.  
  
-   Na deserializacji mapowania zwracanego przez tę metodę jest używany przez element serializujący do deserializacji do wystąpienia typu zastępczego. Następnie wywołuje <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> do przekształcania surrogated wystąpienia wystąpienie oryginalnego typu.  
  
-   Podczas eksportowania typ zastępczy zwracanego przez tę metodę jest odzwierciedlana można pobrać kontraktu danych do użycia podczas generowania metadanych.  
  
-   Przy imporcie typ początkowej jest zmieniany na typ zastępczy, który jest odzwierciedlana można pobrać kontraktu danych dla celów, takich jak odwołujące się do pomocy technicznej.  
  
 <xref:System.Type> Parametr jest typem obiektu, które jest serializowana, po deserializacji, zaimportowanych lub wyeksportowany. <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> Metoda musi zwracać typ danych wejściowych, jeśli surogatu nie obsługuje tego typu. W przeciwnym razie Zwróć odpowiedni typ surrogated. Jeśli istnieje kilka typów zastępczych, można zdefiniować wiele mapowań, w przypadku tej metody.  
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> Metoda nie jest wywoływana dla danych wbudowane kontraktu podstawowych, takich jak <xref:System.Int32> lub <xref:System.String>. Dla innych typów, takich jak tablice, typy zdefiniowane przez użytkownika i innych struktur danych ta metoda zostanie wywołana dla każdego typu.  
  
 W poprzednim przykładzie metoda sprawdza, czy `type` parametru i `Inventory` są porównywalne. Jeśli więc metoda mapowany do `InventorySurrogated`. Zawsze, gdy serializacji nosi nazwę deserializacji, schemat importu lub eksportu schematu, ta funkcja jest wywoływana najpierw, aby określić mapowanie między typami.  
  
### <a name="getobjecttoserialize-method"></a>Metoda GetObjectToSerialize  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> Metoda konwertuje oryginalne wystąpienie typu do wystąpienia typu surogatem. Metoda jest wymagany do serializacji.  
  
 Następnym krokiem jest zdefiniowanie sposób danych fizycznych będą zamapowane z oryginalnego wystąpienia surogatu implementując <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> metody. Na przykład:  
  
 [!code-csharp[C_IDataContractSurrogate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#4)]  
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> Metoda jest wywoływana, gdy obiekt jest serializowany. Ta metoda przesyła dane z oryginalnego typu do pól typu surrogated. Pola, które mogą być bezpośrednio mapowane na pola zastępczych lub manipulacje oryginalne dane mogą być przechowywane w surogatu. Niektóre możliwe zastosowania to: bezpośrednie mapowanie pól, wykonywanie operacji na danych, które mają być przechowywane w polach surrogated lub przechowywania XML oryginalnego typu w polu surrogated.  
  
 `targetType` Parametr odnosi się do zadeklarowanym typem elementu członkowskiego. Ten parametr jest surrogated typ zwracany przez <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> metody. Serializator nie wymusza można przypisać do tego typu to obiekt zwrócony. `obj` Parametru jest obiekt do zserializowania i zostaną przekonwertowane na jego zastępczy, jeśli to konieczne. Ta metoda musi zwracać obiektu wejściowego, jeśli surrogated nie obsługuje obiektu. W przeciwnym razie nowy obiekt zastępczy zostanie zwrócony. Zastępczy nie jest wywoływana, jeśli obiekt ma wartość null. Wiele mapowań zastępczych dla różnych wystąpień może być zdefiniowana w ramach tej metody.  
  
 Podczas tworzenia <xref:System.Runtime.Serialization.DataContractSerializer>, możesz wydać polecenie go, aby zachować odwołania do obiektu. (Aby uzyskać więcej informacji, zobacz [serializacji i deserializacji](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).) Jest to realizowane przez ustawienie `preserveObjectReferences` parametru w jego konstruktorze do `true`. W takim przypadku surogatu zostanie wywołana tylko raz dla obiektu, ponieważ wszystkie kolejne serializations wystarczy napisać odwołanie do strumienia. Jeśli `preserveObjectReferences` ustawiono `false`, a następnie surogatu jest wywoływana za każdym razem, gdy wystąpienie zostanie osiągnięty.  
  
 Typ wystąpienia serializacji różni się od zadeklarowanym typem, informacje o typie zostanie zapisane strumienia, na przykład `xsi:type` umożliwia wystąpienia, które ma zostać przeprowadzona na drugim końcu. Ten proces odbywa się, czy obiekt jest surogatem, czy nie.  
  
 W powyższym przykładzie przekształca dane `Inventory` w przypadku wystąpienia `InventorySurrogated`. On sprawdza, czy typ obiektu i wykonuje niezbędne operacje można przekonwertować na typ surrogated. W tym przypadku pola `Inventory` klasy bezpośrednio są kopiowane do `InventorySurrogated` klasy pola.  
  
### <a name="getdeserializedobject-method"></a>Metoda GetDeserializedObject  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> Metoda konwertuje wystąpienie typu surogatem do oryginalnego wystąpienia typu. Jest ona wymagana do deserializacji.  
  
 Kolejnym krokiem jest określić sposób, w których danych fizycznych będą mapowane z wystąpienia zastępczy oryginalnej. Na przykład:  
  
 [!code-csharp[C_IDataContractSurrogate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#5)]  
  
 Ta metoda jest wywoływana tylko podczas deserializacji obiektu. Zapewnia mapowanie danych odwrotnej do deserializacji z typu zastępczego powrót do oryginalnego typu. Podobnie jak `GetObjectToSerialize` metody, niektóre możliwe zastosowania mogą być bezpośrednio wymiany pola danych, wykonywać operacje na danych i przechowywania danych XML. Podczas deserializacji, użytkownik może nie zawsze uzyskać dokładnych danych wartości od pierwotnego ze względu na manipulacje podczas konwersji danych.  
  
 `targetType` Parametr odnosi się do zadeklarowanym typem elementu członkowskiego. Ten parametr jest surrogated typ zwracany przez `GetDataContractType` metody. `obj` Parametr odnosi się do obiektu, który ma zostać przeprowadzona. Może zostać skonwertowany obiekt powrót do oryginalnego typu, jeśli jest on surogatem. Ta metoda zwraca obiekt wejściowy, jeśli surogatu nie obsługuje obiektu. W przeciwnym razie po deserializacji obiektu zostanie zwrócona po zakończeniu jego konwersji. Jeśli istnieje kilka typów zastępczych, możesz podać Konwersja danych z zastępczy na podstawowy typ dla każdego, wskazując każdego typu i jego konwersji.  
  
 Gdy zwracany jest obiektem, obiekt wewnętrzny tabel są aktualizowane przy użyciu obiektu zwróconego przez ten zastępczy. Wszystkie kolejne odwołania do wystąpienia osiągnie surrogated wystąpienia z tabel obiektu.  
  
 Poprzedni przykład konwertuje obiekty typu `InventorySurrogated` powrócić do początkowej typu `Inventory`. W tym przypadku dane są przesyłane bezpośrednio z `InventorySurrogated` do odpowiednich pól w programie `Inventory`. Ponieważ nie zawiera żadnych danych manipulacje, wszystkich pól członka będzie zawierać te same wartości przed serializacji.  
  
### <a name="getcustomdatatoexport-method"></a>GetCustomDataToExport Method  
 Podczas eksportowania schematu, <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A> jest opcjonalne. Służy do wstawić dodatkowe dane lub wskazówki do wyeksportowanego schematu. Dodatkowe dane mogą być wstawiane na poziomie elementu członkowskiego lub typu. Na przykład:  
  
 [!code-csharp[C_IDataContractSurrogate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#6)]  
  
 Tej metody (za pomocą dwa przeciążenia) umożliwia dołączenie dodatkowych informacji do metadanych na poziomie elementu członkowskiego lub typu. Istnieje możliwość obejmują wskazówek na temat tego, czy składnik jest publiczną lub prywatną i komentarze, które będą zachowane w całym eksportu i importu schematu. Takie informacje zostałyby utracone bez tej metody. Ta metoda nie powoduje wstawiania lub usuwania elementów członkowskich i typy, ale raczej dodaje dodatkowe dane do schematów w jednej z tych poziomów.  
  
 Metoda jest przeciążona i może zająć jedną `Type` (`clrtype` parametr) lub <xref:System.Reflection.MemberInfo> (`memberInfo` parametru). Drugi parametr jest zawsze `Type` (`dataContractType` parametru). Ta metoda jest wywoływana dla każdego elementu członkowskiego i typu surogatem `dataContractType` typu.  
  
 Jedną z tych przeciążeń musi zwracać albo `null` lub możliwe do serializacji obiektu. Obiekt inną niż null będzie serializowana jako adnotacja do wyeksportowanego schematu. Aby uzyskać `Type` przeciążenia każdego typu, który jest eksportowany do schematu są wysyłane do tej metody w pierwszym parametrze wraz z surrogated typ jako `dataContractType` parametru. Dla `MemberInfo` przeciążenia, każdy element członkowski, który jest eksportowany do schematu wysyła informacje jako `memberInfo` parametr typu surrogated w drugim parametrze.  
  
#### <a name="getcustomdatatoexport-method-type-type"></a>Metoda GetCustomDataToExport (typ; typ)  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Type%2CSystem.Type%29?displayProperty=nameWithType> Metoda jest wywoływana podczas eksportowania schematu dla każdej definicji typu. Metoda dodaje informacje do typów w schemacie podczas eksportowania. Każdy zdefiniowany typ są wysyłane do tej metody do ustalenia, czy istnieją dodatkowe dane, które musi być uwzględniony w schemacie.  
  
#### <a name="getcustomdatatoexport-method-memberinfo-type"></a>Metoda GetCustomDataToExport (MemberInfo, typ)  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=nameWithType> Jest wywoływana podczas eksportu dla każdego członka w typach, które są eksportowane. Ta funkcja umożliwia dostosowywanie wszelkie komentarze dla elementów członkowskich, które zostaną uwzględnione w schemacie podawane podczas eksportowania. Informacje dla każdego elementu członkowskiego w klasie są wysyłane do tej metody, aby sprawdzić, czy wszystkie dodatkowe dane mają zostać dodane w schemacie.  
  
 Przykład powyżej wyszukuje `dataContractType` dla każdego elementu członkowskiego surogatu. Zwraca modyfikator dostępu dla każdego pola. Bez tego dostosowania wartością domyślną dla modyfikatory dostępu jest publiczny. W związku z tym wszystkie elementy członkowskie będą zdefiniowane jako publiczny w kodzie, który został wygenerowany za pomocą wyeksportowanego schematu, niezależnie od tego, jakie są ograniczenia ich rzeczywistego dostępu. Bez korzystania z tej implementacji elementu członkowskiego `numpens` jest publiczna w schemacie wyeksportowanego nawet, jeśli została zdefiniowana w zastępczy jako prywatny. Przy użyciu tej metody w schemacie wyeksportowanego modyfikator dostępu mogą być generowane jako prywatny.  
  
### <a name="getreferencedtypeonimport-method"></a>Metoda GetReferencedTypeOnImport  
 Ta metoda mapuje <xref:System.Type> z surogatu do oryginalnego typu. Ta metoda jest opcjonalny w przypadku Importowanie schematu.  
  
 Podczas tworzenia zastępczy, który Importuje schemat i generuje dla niego kod, kolejnym krokiem jest do definiowania typu wystąpienia zastępczy do oryginalnego typu.  
  
 Jeśli wygenerowany kod musi odwoływać się do istniejącego typu użytkownika, odbywa się przez zaimplementowanie <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> metody.  
  
 Podczas importowania schematu, ta metoda jest wywoływana dla każdej deklaracji typu do mapowania typu kontraktu danych surogatem. Parametry ciągu `typeName` i `typeNamespace` zdefiniować nazwę i przestrzeń nazw surrogated typu. Wartość zwracana dla <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> służy do określania, czy nowy typ musi zostać wygenerowane. Ta metoda musi zwracać prawidłowy typ lub wartość null. Prawidłowe typy typ zwracany będzie służyć jako odwołanie typu w wygenerowanym kodzie. Jeśli zwracana jest wartość null, będzie można odwoływać się bez typu i musi zostać utworzony nowy typ. Jeśli istnieje kilka surogaty, jest możliwe przeprowadzenie mapowania dla każdego typu zastępczego do typu początkowej.  
  
 `customData` Parametru jest obiektem, który został pierwotnie zwróciło <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A>. To `customData` jest używany podczas autorzy zastępczy ma zostać wstawiony dodatkowych danych/wskazówki do metadanych do użycia podczas importowania do generowania kodu.  
  
### <a name="processimportedtype-method"></a>Metoda ProcessImportedType  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.ProcessImportedType%2A> Metoda dostosowuje dowolnego typu, utworzone na podstawie Importowanie schematu. Ta metoda jest opcjonalne.  
  
 Podczas importowania schematu, ta metoda umożliwia zaimportowanych informacji typu i kompilacji, które można dostosować. Na przykład:  
  
 [!code-csharp[C_IDataContractSurrogate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#7)]  
  
 Podczas importowania ta metoda jest wywoływana dla każdego typu wygenerowany. Zmień określonego <xref:System.CodeDom.CodeTypeDeclaration> lub zmodyfikować <xref:System.CodeDom.CodeCompileUnit>. Obejmuje to zmianę nazwy, elementy członkowskie, atrybuty i wiele innych właściwości `CodeTypeDeclaration`. Przez przetwarzanie `CodeCompileUnit`, istnieje możliwość modyfikowania dyrektywy, przestrzenie nazw, przywoływanych zestawach i kilka innych aspektów.  
  
 `CodeTypeDeclaration` Parametr zawiera kod DOM deklaracji typu. `CodeCompileUnit` Parametr umożliwia modyfikowanie do przetwarzania kodu.  Zwracanie `null` wyniki w deklaracji typu zostanie odrzucony. Z drugiej strony gdy zwracany jest `CodeTypeDeclaration`, zmiany zostaną zachowane.  
  
 Niestandardowe dane są wstawiane podczas eksportowania metadanych, potrzebny udostępniany użytkownikowi podczas importowania, dzięki czemu mogą być używane. Te dane niestandardowe może służyć do programowania wskazówki modelu lub innych komentarzy. Każdy `CodeTypeDeclaration` i <xref:System.CodeDom.CodeTypeMember> wystąpienie zawiera dane niestandardowe jako <xref:System.CodeDom.CodeObject.UserData%2A> właściwości rzutować `IDataContractSurrogate` typu.  
  
 W powyższym przykładzie wykonuje pewne zmiany w schemacie, zaimportowane. Kod zachowuje prywatne składowe oryginalnego typu za pomocą zastępczych. Modyfikator dostępu domyślne podczas importowania schematu jest `public`. W związku z tym wszyscy członkowie schematu zastępczy będą widoczne publicznie, o ile nie zmodyfikowano, jak w poniższym przykładzie. Podczas eksportowania niestandardowe dane są wstawiane do metadanych o tym, które elementy członkowskie są prywatne. Przykład wyszukuje dane niestandardowe, sprawdza, czy modyfikator dostępu jest prywatny, a następnie modyfikuje właściwego członka na prywatny, ustawiając jego atrybuty. Bez tego dostosowania `numpens` element członkowski byłoby zdefiniowane jako publiczna a nie prywatne.  
  
### <a name="getknowncustomdatatypes-method"></a>Metoda GetKnownCustomDataTypes  
 Ta metoda uzyskuje niestandardowe typy danych zdefiniowane w schemacie. Metoda jest opcjonalny w przypadku Importowanie schematu.  
  
 Metoda jest wywoływana po rozpoczęciu schematu eksportu i importu. Metoda zwraca niestandardowe typy danych używany w schemacie wyeksportowania lub zaimportowania. Metoda jest przekazywana <xref:System.Collections.ObjectModel.Collection%601> ( `customDataTypes` parametru), który jest kolekcją typów. Metoda należy dodać dodatkowe znanych typów, z tą kolekcją. Znane niestandardowe typy danych są wymagane do włączenia serializacji i deserializacji niestandardowych danych przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer>. Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="implementing-a-surrogate"></a>Implementowanie zastępczy  
 Aby korzystać z surogatu kontraktu danych w ramach usługi WCF, należy wykonać kilka specjalnych procedur.  
  
### <a name="to-use-a-surrogate-for-serialization-and-deserialization"></a>Na potrzeby surogatu serializacji i deserializacji  
 Użyj <xref:System.Runtime.Serialization.DataContractSerializer> do wykonywania serializacji i deserializacji obiektu danych z surogatu. <xref:System.Runtime.Serialization.DataContractSerializer> Jest tworzony przez <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>. Surogatu musi być także określona.  
  
##### <a name="to-implement-serialization-and-deserialization"></a>Aby zaimplementować serializacji i deserializacji  
  
1. Utwórz wystąpienie obiektu <xref:System.ServiceModel.ServiceHost> dla Twojej usługi. Aby uzyskać pełne instrukcje, zobacz [programowanie WCF Basic](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
2. Dla każdego <xref:System.ServiceModel.Description.ServiceEndpoint> hosta określonej usługi, Znajdź jego <xref:System.ServiceModel.Description.OperationDescription>.  
  
3. Przeszukaj zachowania operację, aby określić, czy wystąpienie <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> zostanie znaleziony.  
  
4. Jeśli <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> jest znaleziono, ustaw jego <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> właściwość nowe wystąpienie klasy zastępcze. Jeśli nie <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> jest znaleźć, a następnie utwórz nowe wystąpienie i ustawić <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> członkiem nowe zachowanie do nowego wystąpienia surogatu.  
  
5. Na koniec Dodaj to nowe zachowanie do zachowania bieżącej operacji, jak pokazano w poniższym przykładzie:  
  
     [!code-csharp[C_IDataContractSurrogate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#8)]  
  
### <a name="to-use-a-surrogate-for-metadata-import"></a>Do użycia zastępczego w celu zaimportowania metadanych  
 Podczas importowania metadanych, takich jak WSDL i XSD, aby wygenerować kod po stronie klienta, należy dodać do składnika odpowiedzialny za generowanie kodu na podstawie schematu XSD surogatu <xref:System.Runtime.Serialization.XsdDataContractImporter>. Aby to zrobić, należy bezpośrednio zmodyfikować <xref:System.ServiceModel.Description.WsdlImporter> użytej do zaimportowania metadanych.  
  
##### <a name="to-implement-a-surrogate-for-metadata-importation"></a>Aby zaimplementować surogatu Importowanie metadanych  
  
1. Importowanie przy użyciu metadanych <xref:System.ServiceModel.Description.WsdlImporter> klasy.  
  
2. Użyj <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metodę sprawdzania, czy <xref:System.Runtime.Serialization.XsdDataContractImporter> został zdefiniowany.  
  
3. Jeśli <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metoda zwraca `false`, Utwórz nową <xref:System.Runtime.Serialization.XsdDataContractImporter> i ustaw jego <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> właściwość nowe wystąpienie klasy <xref:System.Runtime.Serialization.ImportOptions> klasy. W przeciwnym razie użyj importera zwrócony przez `out` parametru <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metody.  
  
4. Jeśli <xref:System.Runtime.Serialization.XsdDataContractImporter> nie ma przypisanego <xref:System.Runtime.Serialization.ImportOptions> zdefiniowane, a następnie ustaw właściwość jako nowe wystąpienie klasy <xref:System.Runtime.Serialization.ImportOptions> klasy.  
  
5. Ustaw <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A> właściwość <xref:System.Runtime.Serialization.ImportOptions> z <xref:System.Runtime.Serialization.XsdDataContractImporter> do nowego wystąpienia surogatu.  
  
6. Dodaj <xref:System.Runtime.Serialization.XsdDataContractImporter> do kolekcji zwróconej przez <xref:System.ServiceModel.Description.MetadataExporter.State%2A> właściwość <xref:System.ServiceModel.Description.WsdlImporter> (odziedziczone <xref:System.ServiceModel.Description.MetadataExporter> klasy.)  
  
7. Użyj <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> metody <xref:System.ServiceModel.Description.WsdlImporter> Aby zaimportować wszystkie kontrakty danych w schemacie. Podczas ostatniego kroku generowania kodu ze schematów załadowany przez wywołanie surogatu.  
  
     [!code-csharp[C_IDataContractSurrogate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#9)]  
  
### <a name="to-use-a-surrogate-for-metadata-export"></a>Zastępczy na potrzeby eksportowania metadanych  
 Domyślnie, gdy Eksportowanie metadanych z usługi WCF na potrzeby usługi schemat WSDL i XSD musi zostać wygenerowane. Surogatu musi zostać dodane do składnika odpowiedzialny za generowanie schematu XSD do typów kontraktu danych, <xref:System.Runtime.Serialization.XsdDataContractExporter>. Aby to zrobić, użyj zachowanie, który implementuje <xref:System.ServiceModel.Description.IWsdlExportExtension> do modyfikowania <xref:System.ServiceModel.Description.WsdlExporter>, lub bezpośrednio zmodyfikować <xref:System.ServiceModel.Description.WsdlExporter> umożliwia eksportowanie metadanych.  
  
##### <a name="to-use-a-surrogate-for-metadata-export"></a>Zastępczy na potrzeby eksportowania metadanych  
  
1. Utwórz nową <xref:System.ServiceModel.Description.WsdlExporter> lub użyj `wsdlExporter` parametr przekazany do <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> metody.  
  
2. Użyj <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> funkcji, aby sprawdzić, czy <xref:System.Runtime.Serialization.XsdDataContractExporter> został zdefiniowany.  
  
3. Jeśli <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> zwraca `false`, Utwórz nową <xref:System.Runtime.Serialization.XsdDataContractExporter> za pomocą wygenerowanego schematów XML z <xref:System.ServiceModel.Description.WsdlExporter>i dodaj go do kolekcji zwróconej przez <xref:System.ServiceModel.Description.MetadataExporter.State%2A> właściwość <xref:System.ServiceModel.Description.WsdlExporter>. W przeciwnym razie użyj eksportera, zwrócone przez `out` parametru <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metody.  
  
4. Jeśli <xref:System.Runtime.Serialization.XsdDataContractExporter> nie ma przypisanego <xref:System.Runtime.Serialization.ExportOptions> zdefiniowane, a następnie ustaw <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> właściwość nowe wystąpienie klasy <xref:System.Runtime.Serialization.ExportOptions> klasy.  
  
5. Ustaw <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A> właściwość <xref:System.Runtime.Serialization.ExportOptions> z <xref:System.Runtime.Serialization.XsdDataContractExporter> do nowego wystąpienia surogatu. Kolejnych kroków eksportowania metadanych nie wymagają zmiany.  
  
     [!code-csharp[C_IDataContractSurrogate#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#10)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.IDataContractSurrogate>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.Runtime.Serialization.ImportOptions>
- <xref:System.Runtime.Serialization.ExportOptions>
- [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
