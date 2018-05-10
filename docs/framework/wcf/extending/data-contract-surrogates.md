---
title: Surogaty kontraktu danych
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], surrogates
ms.assetid: 8c31134c-46c5-4ed7-94af-bab0ac0dfce5
ms.openlocfilehash: b06cb45d6075c8de1da973a11e2edec6792df304
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="data-contract-surrogates"></a>Surogaty kontraktu danych
Kontrakt danych *Surogat* jest funkcją zaawansowaną oparty na modelu kontraktu danych. Ta funkcja służy do zastosowania w przypadku dostosowania typu i podstawienia w sytuacjach, w którym użytkownicy chcesz zmienić, jak serializacji typu zdeserializowany lub planowane w metadanych. Sytuacje, w którym mogą być używane surogatu jest gdy kontrakt danych nie został określony dla typów, pól i właściwości nie są oznaczone ikoną z <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu lub użytkownicy mają być dynamicznie utworzyć zmian schematu.  
  
 Serializacja i deserializacja są realizowane przy użyciu surogatu kontraktu danych, korzystając z <xref:System.Runtime.Serialization.DataContractSerializer> przekonwertować z .NET Framework na odpowiedni format, takich jak XML. Zastępcza kontraktu danych może również służyć do modyfikowania metadanych wyeksportowane dla typów, podczas produkowania reprezentacje metadanych, takich jak dokumenty schematu XML (XSD). Po zaimportowaniu kodu jest tworzona na podstawie metadanych i surogatu można w takim przypadku można dostosować również wygenerowany kod.  
  
## <a name="how-the-surrogate-works"></a>Jak działa surogatu  
 Surogatu działa przez mapowanie jeden typ ("oryginalny" typ) do innego typu (typu "surrogated"). W poniższym przykładzie przedstawiono oryginalny typ `Inventory` i nowych Surogat `InventorySurrogated` typu. `Inventory` Typ nie jest możliwy do serializacji, ale `InventorySurrogated` jest typu:  
  
 [!code-csharp[C_IDataContractSurrogate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#1)]  
  
 Ponieważ kontrakt danych nie został zdefiniowany dla tej klasy, przekonwertować klasę Klasa zastępcza z kontraktu danych. W poniższym przykładzie pokazano surrogated klasy:  
  
 [!code-csharp[C_IDataContractSurrogate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#2)]  
  
## <a name="implementing-the-idatacontractsurrogate"></a>Implementowanie IDataContractSurrogate  
 Aby korzystać z surogatu kontraktu danych, zaimplementuj <xref:System.Runtime.Serialization.IDataContractSurrogate> interfejsu.  
  
 Poniżej przedstawiono omówienie poszczególnych metod <xref:System.Runtime.Serialization.IDataContractSurrogate> z implementacją możliwe.  
  
### <a name="getdatacontracttype"></a>GetDataContractType  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> Metoda mapuje jednego typu na inny. Ta metoda jest wymagana do serializacji, deserializacji importu i eksportu.  
  
 Pierwszym zadaniem jest zdefiniowanie, jakie typy będą zamapowane na inne typy. Na przykład:  
  
 [!code-csharp[C_IDataContractSurrogate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#3)]  
  
-   Na serializacji, mapowania zwracane przez tę metodę jest następnie używany do transformacji oryginalne wystąpienie do wystąpienia surrogated przez wywołanie metody <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> metody.  
  
-   Podczas deserializacji mapowanie zwracane przez tę metodę jest używany przez serializator do deserializacji do wystąpienia typu zastępczego. Następnie wywołuje <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> do przekształcania surrogated wystąpienia na wystąpienie oryginalnego typu.  
  
-   Podczas eksportowania Surogat zwrócone przez tę metodę jest widoczna uzyskanie kontraktu danych do użycia podczas generowania metadanych.  
  
-   Podczas importowania typ początkowej jest zmieniany na typu zastępczego, który jest widoczny uzyskanie kontraktu danych do użycia dla celów, takich jak odwołujące się do pomocy technicznej.  
  
 <xref:System.Type> Parametr jest typu obiektu, który jest serializowana, w zdeserializowany, eksportowany lub importowany. <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> Metoda musi zwracać typ danych wejściowych, jeśli surogatu nie obsługuje tego typu. W przeciwnym razie zwraca surrogated odpowiedniego typu. Jeśli istnieje kilka typów Surogat, można zdefiniować wiele mapowań w ramach tej metody.  
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> Metoda nie jest wywoływana dla wbudowanych danych podstawowych kontraktu, takich jak <xref:System.Int32> lub <xref:System.String>. Dla innych typów, takich jak tablice, typy danych zdefiniowane przez użytkownika i inne struktury danych ta metoda zostanie wywołana dla każdego typu.  
  
 W poprzednim przykładzie metoda sprawdza, czy `type` parametru i `Inventory` mogą być porównywane. Jeśli tak, metoda jest mapowany na `InventorySurrogated`. W przypadku, gdy serializacji, nosi nazwę deserializacji, schemat importowania lub eksportowania schematu, ta funkcja jest wywoływana najpierw w celu określenia mapowania między typami.  
  
### <a name="getobjecttoserialize-method"></a>GetObjectToSerialize — metoda  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> Metoda konwertuje oryginalne wystąpienie typu do wystąpienia typu element zastępczy. Metoda jest wymagana do serializacji.  
  
 Następnym krokiem jest zdefiniowanie sposób fizycznej dane zostaną zmapowane z oryginalnego wystąpienia do surogatu zaimplementowanie <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> metody. Na przykład:  
  
 [!code-csharp[C_IDataContractSurrogate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#4)]  
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> Metoda jest wywoływana, gdy serializowany jest obiekt. Tej metody transferu danych z oryginalnego typu do pól typu surrogated. Pola, które mogą być bezpośrednio mapowane na dwuskładnikowy pól lub manipulacje oryginalnych danych może być przechowywany w surogatu. Niektóre możliwe zastosowania obejmują: bezpośrednie mapowanie pól, wykonywanie operacji na danych, które mają być przechowywane w polach surrogated lub przechowywania XML oryginalny typ w polu surrogated.  
  
 `targetType` Parametr odnosi się do zadeklarowanym typem elementu członkowskiego. Ten parametr jest surrogated typem zwracanym przez <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> metody. Serializator nie obsługuje wymuszania czy obiektu zwróconego jest możliwa do przypisania do tego typu. `obj` Parametr jest obiekt do zserializowania i zostanie skonwertowana do jego Surogat, jeśli to konieczne. Ta metoda musi zwracać obiekt wejściowy, jeśli surrogated nie obsługuje obiektu. W przeciwnym razie nowy obiekt Surogat zostaną zwrócone. Surogatu nie jest wywoływana, gdy obiekt ma wartość null. Wiele mapowań dwuskładnikowego dla innych wystąpień może zostać zdefiniowany w ramach tej metody.  
  
 Podczas tworzenia <xref:System.Runtime.Serialization.DataContractSerializer>, można zmodyfikować go, aby zachować odwołania do obiektów. (Aby uzyskać więcej informacji, zobacz [serializacji i deserializacji](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).) Odbywa się przez ustawienie `preserveObjectReferences` parametru w jego konstruktora `true`. W takim przypadku surogatu zostanie wywołana tylko raz dla obiektu, ponieważ wszystkie kolejne serializations zapisu tylko odwołanie do strumienia. Jeśli `preserveObjectReferences` ma ustawioną wartość `false`, a następnie surogatu jest wywoływana za każdym razem, gdy napotkano wystąpienia.  
  
 Jeśli typ serializacji wystąpienia różni się od deklarowanego typu, typu informacje są zapisywane do strumienia, na przykład `xsi:type` umożliwia wystąpienia można deserializować na drugim końcu. Ten proces, czy obiekt jest element zastępczy lub nie.  
  
 W powyższym przykładzie konwertuje dane z `Inventory` wystąpienia elementu `InventorySurrogated`. Sprawdza typ obiektu, a wykonuje niezbędne operacje można przekonwertować na typ surrogated. W tym przypadku pola `Inventory` klasy bezpośrednio są kopiowane do `InventorySurrogated` klasy pól.  
  
### <a name="getdeserializedobject-method"></a>GetDeserializedObject — metoda  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> Metoda konwertuje wystąpienie typu element zastępczy do oryginalnego wystąpienia typu. Jest wymagany przy deserializacji.  
  
 Następnym zadaniem jest określenie sposobu fizycznego dane zostaną zmapowane z wystąpienia elementu zastępczego oryginalnej. Na przykład:  
  
 [!code-csharp[C_IDataContractSurrogate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#5)]  
  
 Ta metoda jest wywoływana tylko podczas deserializacji obiektu. Zapewnia mapowanie danych odwrotnej do deserializacji z typu zastępczego przywracając jego oryginalny typ. Podobnie jak `GetObjectToSerialize` niektóre możliwe zastosowania metody, może być bezpośrednio wymiany pola danych, wykonywać operacje na danych i przechowywanie danych XML. Podczas deserializacji, użytkownik może nie zawsze uzyskać wartości dokładne dane z oryginalnej z powodu manipulacji podczas konwersji danych.  
  
 `targetType` Parametr odnosi się do zadeklarowanym typem elementu członkowskiego. Ten parametr jest surrogated typem zwracanym przez `GetDataContractType` metody. `obj` Parametr odwołuje się do obiektu, który został zdeserializowany. Obiekt może zostać przekonwertowany przywracając jego oryginalny typ, jeśli jest element zastępczy. Ta metoda zwraca obiekt wejściowy, jeśli surogatu nie obsługuje obiektu. W przeciwnym razie zdeserializowany obiekt zostanie zwrócona po zakończeniu jego konwersji. Jeśli istnieje kilka typów Surogat, musisz podać Konwersja danych z surogatu do typu podstawowego dla każdego wskazując każdego typu i jego konwersji.  
  
 Podczas zwrócenie obiektu, obiekt wewnętrzny tabel są aktualizowane przy obiektu zwracanego przez ten Surogat. Wszystkie kolejne odwołania do wystąpienia uzyska surrogated wystąpienia z tabel obiektu.  
  
 Poprzedni przykład konwertuje obiekty typu `InventorySurrogated` do początkowej typu `Inventory`. W takim przypadku dane są przesyłane bezpośrednio z `InventorySurrogated` do odpowiednich pól w `Inventory`. Ponieważ nie ma żadnych manipulacji danych, wszystkie pola elementu członkowskiego będzie zawierać takie same wartości jak przed serializacji.  
  
### <a name="getcustomdatatoexport-method"></a>GetCustomDataToExport — metoda  
 Podczas eksportowania schematu, <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A> jest opcjonalne. Służy do wstawienia dodatkowe dane lub wskazówek do wyeksportowanego schematu. Dodatkowe dane mogą być wstawiane na poziomie elementu członkowskiego lub typu. Na przykład:  
  
 [!code-csharp[C_IDataContractSurrogate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#6)]  
  
 Tę metodę (z dwa przeciążenia) umożliwia uwzględnienie dodatkowych informacji w metadanych, albo na poziomie elementu członkowskiego lub typu. Istnieje możliwość zawierające wskazówki dotyczące tego, czy element członkowski jest publiczny lub prywatny i uwagi, które będą zachowane w ramach eksportowania i importowania schematu. Tych informacji może spowodować utratę bez tej metody. Ta metoda nie powoduje wstawiania lub usuwania elementów członkowskich lub typów, ale raczej dodaje dodatkowe dane do schematów w jednej z tych poziomów.  
  
 Metody jest przeciążona i może trwać albo `Type` (`clrtype` parametru) lub <xref:System.Reflection.MemberInfo> (`memberInfo` parametru). Drugi parametr jest zawsze `Type` (`dataContractType` parametru). Ta metoda jest wywoływana dla każdego elementu członkowskiego i typ element zastępczy `dataContractType` typu.  
  
 Jedną z tych przeciążenia musi zwracać `null` lub do serializacji obiektu. Obiekt zerowy będą wykonywane szeregowo jako adnotacji do wyeksportowanego schematu. Aby uzyskać `Type` przeciążeniu każdego typu, który został wyeksportowany do schematu są wysyłane do tej metody w pierwszym parametrze wraz z typem surrogated jako `dataContractType` parametru. Aby uzyskać `MemberInfo` przeciążenia, każdy element członkowski, który został wyeksportowany do schematu wysyła informacje jako `memberInfo` parametru typu surrogated w drugi parametr.  
  
#### <a name="getcustomdatatoexport-method-type-type"></a>Metoda GetCustomDataToExport (Type, typ)  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Type%2CSystem.Type%29?displayProperty=nameWithType> Metoda jest wywoływana podczas eksportowania schematu dla każdej definicji typu. Metoda dodaje informacje do typów w ramach schematu podczas eksportowania. Każdy typ zdefiniowany są wysyłane do tej metody do ustalenia, czy istnieją dodatkowe dane, które musi być uwzględniony w schemacie.  
  
#### <a name="getcustomdatatoexport-method-memberinfo-type"></a>Metoda GetCustomDataToExport (MemberInfo, typ)  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=nameWithType> Jest wywoływana podczas eksportu dla każdego elementu w typach, które zostaną wyeksportowane. Ta funkcja umożliwia dostosowanie wszelkie komentarze do elementów członkowskich, które zostaną uwzględnione w schemacie podczas eksportu. Informacje dla każdego elementu w obrębie tej klasy są wysyłane do tej metody do sprawdzenia, czy wszystkie dodatkowe dane mają zostać dodane w schemacie.  
  
 Przykład powyżej wyszukiwanie za pomocą `dataContractType` dla każdego elementu członkowskiego surogatu. Zwraca modyfikator dostępu właściwe dla każdego pola. Bez tego dostosowania wartością domyślną dla modyfikatory dostępu jest publiczny. W związku z tym wszystkie elementy członkowskie byłoby zdefiniowane jako public w kodzie, wygenerowane za pomocą wyeksportowanego schematu niezależnie od tego, jakie są ograniczenia ich rzeczywistego dostępu. Jeśli nie przy użyciu tej implementacji element członkowski `numpens` jest publiczna w schemacie wyeksportowanego nawet jeśli została zdefiniowana w surogatu jako prywatny. Przy użyciu tej metody w schemacie wyeksportowanego modyfikator dostępu mogą być generowane jako prywatny.  
  
### <a name="getreferencedtypeonimport-method"></a>GetReferencedTypeOnImport — metoda  
 Ta metoda mapuje <xref:System.Type> z surogatu do oryginalnego typu. Ta metoda jest opcjonalny w przypadku import schematu.  
  
 Podczas tworzenia surogatu, który importuje schematu i generuje dla niego kod, następnego zadania jest określenie typu wystąpienia zastępczego do jego oryginalnej typu.  
  
 Jeśli wygenerowany kod musi odwoływać się istniejący typ użytkownika, w tym celu implementowania <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> metody.  
  
 Podczas importowania schematu, ta metoda jest wywoływana dla każdej deklaracji typu do mapowania typu kontraktu danych element zastępczy. Parametry ciągu `typeName` i `typeNamespace` zdefiniować nazwę i przestrzeń nazw surrogated typu. Wartość zwracana <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> służy do określania, czy nowy typ ma zostać wygenerowany. Ta metoda musi zwracać prawidłowy typ lub wartość null. Prawidłowe typy typ zwracany będzie służyć jako typu występującego w odwołaniu w wygenerowanym kodzie. Jeśli zostanie zwrócona wartość null, żaden typ nie zostanie dodane odwołanie, i musi zostać utworzony nowy typ. Jeśli istnieje kilka części znaku dwuskładnikowego jest można wykonać mapowania dla każdego typu zastępczego do jego typ początkowej.  
  
 `customData` Parametr jest obiekt pierwotnie zwrócony z <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A>. To `customData` jest używany podczas autorów Surogat chcesz wstawić dodatkowych danych/wskazówek do metadanych do użycia podczas importowania do generowania kodu.  
  
### <a name="processimportedtype-method"></a>ProcessImportedType — metoda  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.ProcessImportedType%2A> Metody dostosowuje dowolnego typu utworzone na podstawie schematu import. Ta metoda jest opcjonalne.  
  
 Podczas importowania schematu, ta metoda umożliwia zaimportowanych informacji typu i kompilacji, które można dostosować. Na przykład:  
  
 [!code-csharp[C_IDataContractSurrogate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#7)]  
  
 Podczas importowania ta metoda jest wywoływana dla każdego typu wygenerowany. Zmień określonego <xref:System.CodeDom.CodeTypeDeclaration> lub zmodyfikować <xref:System.CodeDom.CodeCompileUnit>. Obejmuje to zmianę nazwy, elementy członkowskie, atrybuty i wiele innych właściwości `CodeTypeDeclaration`. Przetwarzanie `CodeCompileUnit`, można zmodyfikować dyrektywy, przestrzenie nazw zestawów występujących w odwołaniach i inne aspekty.  
  
 `CodeTypeDeclaration` Parametr zawiera deklarację typu modelu DOM kodu. `CodeCompileUnit` Parametr umożliwia zmianę przetwarzania kodu.  Zwracanie `null` wyniki w deklaracji typu zostanie odrzucony. Z drugiej strony gdy zwracany jest `CodeTypeDeclaration`, zmiany zostaną zachowane.  
  
 Niestandardowe dane są wstawiane podczas eksportowania metadanych, należy podać użytkownikowi podczas importowania, aby można go używać. Te niestandardowe dane może służyć do wskazówek modelu programowania lub innych komentarzy. Każdy `CodeTypeDeclaration` i <xref:System.CodeDom.CodeTypeMember> wystąpienia zawiera niestandardowe dane jako <xref:System.CodeDom.CodeObject.UserData%2A> właściwości rzutować `IDataContractSurrogate` typu.  
  
 W powyższym przykładzie wykonuje pewne zmiany w schemacie zaimportowane. Kod zachowuje prywatne elementy członkowskie oryginalnego typu przy użyciu surogatu. Modyfikator dostępu domyślne podczas importowania schematu jest `public`. W związku z tym wszystkie elementy członkowskie schematu Surogat będzie publiczne, chyba że zmodyfikowany, jak w poniższym przykładzie. Podczas eksportowania danych niestandardowych są wstawiane do metadanych dotyczących elementów członkowskich, które są prywatne. Przykład wyszukuje danych niestandardowych, sprawdza, czy modyfikator dostępu jest prywatny, a następnie modyfikuje odpowiedni element członkowski ma charakter prywatny, ustawiając jego atrybuty. Bez tego dostosowania `numpens` elementu członkowskiego może być zdefiniowana jako publicznego zamiast prywatnych.  
  
### <a name="getknowncustomdatatypes-method"></a>GetKnownCustomDataTypes — metoda  
 Ta metoda uzyskuje niestandardowe typy danych zdefiniowane w schemacie. Metoda jest opcjonalny w przypadku import schematu.  
  
 Metoda jest wywoływana na początku schematu eksportu i importu. Metoda zwraca niestandardowe typy danych używany w schemacie wyeksportowane i zaimportowane. Metoda jest przekazywana <xref:System.Collections.ObjectModel.Collection%601> ( `customDataTypes` parametru), która jest kolekcją typów. Metoda należy dodać dodatkowe znanych typów do tej kolekcji. Znane niestandardowe typy danych są wymagane do włączenia serializacji i deserializacji niestandardowych danych przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer>. Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="implementing-a-surrogate"></a>Implementowanie surogatu  
 Aby korzystać z surogatu kontraktu danych w ramach usługi WCF, należy wykonać kilka specjalnych procedur.  
  
### <a name="to-use-a-surrogate-for-serialization-and-deserialization"></a>Aby użyć surogatu serializacji i deserializacji  
 Użyj <xref:System.Runtime.Serialization.DataContractSerializer> do wykonywania serializacji i deserializacji obiektu danych z surogatu. <xref:System.Runtime.Serialization.DataContractSerializer> Jest tworzony przez <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>. Należy także określić surogatu.  
  
##### <a name="to-implement-serialization-and-deserialization"></a>Aby zaimplementować serializacja i deserializacja  
  
1.  Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> dla usługi. Aby uzyskać pełne instrukcje, zobacz [podstawowe programowania WCF](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
2.  Dla każdego <xref:System.ServiceModel.Description.ServiceEndpoint> hosta określonej usługi, Znajdź jego <xref:System.ServiceModel.Description.OperationDescription>.  
  
3.  Wyszukiwanie za pomocą zachowań operacji, aby ustalić, czy wystąpienie <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> został znaleziony.  
  
4.  Jeśli <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> jest znaleziono, ustaw jej <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> nowe wystąpienie klasy surogatu dla właściwości. Jeśli nie <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> jest znaleziono, Utwórz nowe wystąpienie i ustaw <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> członka do nowego wystąpienia surogatu nowe zachowanie.  
  
5.  Na koniec Dodaj to nowe zachowanie do zachowania bieżącej operacji, jak pokazano w poniższym przykładzie:  
  
     [!code-csharp[C_IDataContractSurrogate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#8)]  
  
### <a name="to-use-a-surrogate-for-metadata-import"></a>Aby użyć surogatu dla importu metadanych  
 Podczas importowania metadanych, takich jak WSDL i XSD, aby wygenerować kod po stronie klienta, musi zostać dodany do składnik odpowiedzialny za generowanie kodu na podstawie schematu XSD surogatu <xref:System.Runtime.Serialization.XsdDataContractImporter>. Aby to zrobić, bezpośrednio modyfikować <xref:System.ServiceModel.Description.WsdlImporter> umożliwia importowanie metadanych.  
  
##### <a name="to-implement-a-surrogate-for-metadata-importation"></a>Aby zaimplementować surogatu Import metadanych  
  
1.  Importuj przy użyciu metadanych <xref:System.ServiceModel.Description.WsdlImporter> klasy.  
  
2.  Użyj <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> , aby sprawdzić, czy <xref:System.Runtime.Serialization.XsdDataContractImporter> została zdefiniowana.  
  
3.  Jeśli <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metoda zwraca `false`, Utwórz nową <xref:System.Runtime.Serialization.XsdDataContractImporter> i ustawić jej <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> właściwości nowe wystąpienie klasy <xref:System.Runtime.Serialization.ImportOptions> klasy. W przeciwnym razie użyj importera zwrócony przez `out` parametr <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metody.  
  
4.  Jeśli <xref:System.Runtime.Serialization.XsdDataContractImporter> nie ma <xref:System.Runtime.Serialization.ImportOptions> zdefiniowana, a następnie ustaw właściwość jako nowe wystąpienie klasy <xref:System.Runtime.Serialization.ImportOptions> klasy.  
  
5.  Ustaw <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A> właściwość <xref:System.Runtime.Serialization.ImportOptions> z <xref:System.Runtime.Serialization.XsdDataContractImporter> do nowego wystąpienia surogatu.  
  
6.  Dodaj <xref:System.Runtime.Serialization.XsdDataContractImporter> do kolekcji zwróconej przez <xref:System.ServiceModel.Description.MetadataExporter.State%2A> właściwość <xref:System.ServiceModel.Description.WsdlImporter> (dziedziczone z <xref:System.ServiceModel.Description.MetadataExporter> klasy.)  
  
7.  Użyj <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> metody <xref:System.ServiceModel.Description.WsdlImporter> Aby zaimportować wszystkie kontraktów danych w schemacie. W ostatnim kroku w celu generowania kodu z załadowanych przez wywołanie surogatu schematów.  
  
     [!code-csharp[C_IDataContractSurrogate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#9)]  
  
### <a name="to-use-a-surrogate-for-metadata-export"></a>Aby użyć surogatu eksportu metadanych  
 Domyślnie podczas eksportowania metadanych z WCF dla usługi schemat zarówno WSDL i XSD ma zostać wygenerowany. Surogatu musi zostać dodany do składnik odpowiedzialny za generowanie schematu XSD dla typy kontraktu danych, <xref:System.Runtime.Serialization.XsdDataContractExporter>. Aby to zrobić, użyj zachowania, który implementuje <xref:System.ServiceModel.Description.IWsdlExportExtension> do modyfikowania <xref:System.ServiceModel.Description.WsdlExporter>, lub bezpośrednio modyfikować <xref:System.ServiceModel.Description.WsdlExporter> używany do eksportowania metadanych.  
  
##### <a name="to-use-a-surrogate-for-metadata-export"></a>Aby użyć surogatu eksportu metadanych  
  
1.  Utwórz nową <xref:System.ServiceModel.Description.WsdlExporter> lub użyj `wsdlExporter` parametr przekazany do <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> metody.  
  
2.  Użyj <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> funkcji, aby sprawdzić, czy <xref:System.Runtime.Serialization.XsdDataContractExporter> została zdefiniowana.  
  
3.  Jeśli <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> zwraca `false`, Utwórz nową <xref:System.Runtime.Serialization.XsdDataContractExporter> z schematów XML wygenerowanych z <xref:System.ServiceModel.Description.WsdlExporter>i dodaj go do kolekcji zwróconej przez <xref:System.ServiceModel.Description.MetadataExporter.State%2A> właściwość <xref:System.ServiceModel.Description.WsdlExporter>. W przeciwnym razie użyj eksportera zwrócony przez `out` parametr <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metody.  
  
4.  Jeśli <xref:System.Runtime.Serialization.XsdDataContractExporter> nie ma <xref:System.Runtime.Serialization.ExportOptions> zdefiniowana, a następnie ustaw <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> właściwości nowe wystąpienie klasy <xref:System.Runtime.Serialization.ExportOptions> klasy.  
  
5.  Ustaw <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A> właściwość <xref:System.Runtime.Serialization.ExportOptions> z <xref:System.Runtime.Serialization.XsdDataContractExporter> do nowego wystąpienia surogatu. Kolejne kroki eksportowania metadanych nie wymagają żadnych zmian.  
  
     [!code-csharp[C_IDataContractSurrogate#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#10)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.IDataContractSurrogate>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.Runtime.Serialization.ImportOptions>  
 <xref:System.Runtime.Serialization.ExportOptions>  
 [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
