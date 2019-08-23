---
title: Importowanie schematu w celu generowania klas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, schema import and export
- XsdDataContractImporter class
ms.assetid: b9170583-8c34-43bd-97bb-6c0c8dddeee0
ms.openlocfilehash: dc33088c3519bfd088ed64a4de087c5086890804
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918482"
---
# <a name="importing-schema-to-generate-classes"></a>Importowanie schematu w celu generowania klas
Aby wygenerować klasy z schematów, które są możliwe do użycia w Windows Communication Foundation (WCF) <xref:System.Runtime.Serialization.XsdDataContractImporter> , użyj klasy. W tym temacie opisano proces i różnice.  
  
## <a name="the-import-process"></a>Proces importowania
 Proces importowania schematu rozpoczyna się od <xref:System.Xml.Schema.XmlSchemaSet> i <xref:System.CodeDom.CodeCompileUnit>tworzy.  
  
 `XmlSchemaSet` Jest częścią .NET Framework modelu obiektów schematu (SOM), który reprezentuje zestaw dokumentów schematu języka definicji schematu XML (XSD). Aby utworzyć `XmlSchemaSet` obiekt z zestawu dokumentów XSD, należy zdeserializować każdy dokument <xref:System.Xml.Schema.XmlSchema> do obiektu (przy użyciu <xref:System.Xml.Serialization.XmlSerializer>) i dodać te obiekty do nowego `XmlSchemaSet`.  
  
 `CodeCompileUnit` Jest częścią Code Document Object Model .NET Framework (CodeDOM), która reprezentuje kod .NET Framework w sposób abstrakcyjny. Aby wygenerować rzeczywisty kod `CodeCompileUnit`z, należy użyć podklasy <xref:System.CodeDom.Compiler.CodeDomProvider> <xref:Microsoft.CSharp.CSharpCodeProvider> klasy, takiej jak lub <xref:Microsoft.VisualBasic.VBCodeProvider> klasy.  
  
### <a name="to-import-a-schema"></a>Aby zaimportować schemat  
  
1. Utwórz wystąpienie <xref:System.Runtime.Serialization.XsdDataContractImporter>obiektu.  
  
2. Opcjonalny. `CodeCompileUnit` Przekaż w konstruktorze. Typy generowane podczas importowania schematu są dodawane do tego `CodeCompileUnit` wystąpienia zamiast od pustego. `CodeCompileUnit`  
  
3. Opcjonalny. Wywołaj jedną z <xref:System.Runtime.Serialization.XsdDataContractImporter.CanImport%2A> metod. Metoda określa, czy dany schemat jest prawidłowym schematem kontraktu danych i może zostać zaimportowany. Metoda ma takie same przeciążenia jak `Import` (Następny krok). `CanImport`  
  
4. Wywołaj jedną z przeciążonych `Import` metod, na przykład <xref:System.Runtime.Serialization.XsdDataContractImporter.Import%28System.Xml.Schema.XmlSchemaSet%29> metodę.  
  
     Najprostszy Przeciążenie pobiera `XmlSchemaSet` i importuje wszystkie typy, w tym typy anonimowe, które znajdują się w tym zestawie schematów. Inne przeciążenia umożliwiają określenie typu XSD lub listy typów do zaimportowania (w formie <xref:System.Xml.XmlQualifiedName> lub `XmlQualifiedName` kolekcji obiektów). W takim przypadku importowane są tylko wybrane typy. Przeciążenie przyjmuje <xref:System.Xml.Schema.XmlSchemaElement> , że importuje określony element z, a także `XmlSchemaSet`związany z nim typ (bez względu na to, czy jest to anonimowe czy nie). To Przeciążenie zwraca obiekt `XmlQualifiedName`, który reprezentuje nazwę kontraktu danych typu wygenerowanego dla tego elementu.  
  
     Wiele wywołań `Import` metody powoduje dodanie wielu elementów do tego samego `CodeCompileUnit`. Typ nie jest generowany w przypadku, `CodeCompileUnit` gdy już istnieje. Wywołaj `Import` wiele razy w tym `XsdDataContractImporter` samym czasie, zamiast `XsdDataContractImporter` używać wielu obiektów. Jest to zalecany sposób, aby uniknąć generowania zduplikowanych typów.  
  
    > [!NOTE]
    > Jeśli wystąpi błąd podczas importowania, `CodeCompileUnit` będzie on w stanie nieprzewidywalnym. `CodeCompileUnit` Użycie wyniku z niepowodzenia importowania może spowodować powstanie luk w zabezpieczeniach.  
  
5. `CodeCompileUnit` Dostęp<xref:System.Runtime.Serialization.XsdDataContractImporter.CodeCompileUnit%2A> do właściwości.  
  
### <a name="import-options-customizing-the-generated-types"></a>Opcje importowania: Dostosowywanie wygenerowanych typów  
 Można ustawić <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> Właściwość <xref:System.Runtime.Serialization.XsdDataContractImporter> nawystąpienieklasywcelukontrolowaniaróżnychaspektówprocesuimportowania.<xref:System.Runtime.Serialization.ImportOptions> Wiele opcji bezpośrednio wpływa na generowane typy.  
  
#### <a name="controlling-the-access-level-generateinternal-or-the-internal-switch"></a>Kontrolowanie poziomu dostępu (GenerateInternal lub przełącznika/Internal)  
 Odnosi się to do przełącznika **/Internal** w narzędziu do narzędzia [metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 Zwykle typy publiczne są generowane ze schematu, z polami prywatnymi i pasujące do właściwości publicznego elementu członkowskiego danych. Aby zamiast tego wygenerować typy wewnętrzne, należy <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A> ustawić właściwość `true`na.  
  
 W poniższym przykładzie przedstawiono schemat przekształcony do klasy wewnętrznej, <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A> gdy właściwość jest ustawiona na`true.`  
  
 [!code-csharp[c_SchemaImportExport#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#2)]
 [!code-vb[c_SchemaImportExport#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#2)]  
  
#### <a name="controlling-namespaces-namespaces-or-the-namespace-switch"></a>Kontrolowanie przestrzeni nazw (przestrzenie nazw lub przełącznik/Namespace)  
 Odnosi się to do przełącznika **/Namespace** w `Svcutil.exe` narzędziu.  
  
 Zwykle typy generowane na podstawie schematu są generowane w .NET Framework przestrzenie nazw, z każdą przestrzeni nazw XSD odpowiadającą określonej przestrzeni nazw .NET Framework zgodnie z mapowaniem opisanym w odwołaniu do [schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Mapowanie można dostosować według <xref:System.Runtime.Serialization.ImportOptions.Namespaces%2A> właściwości <xref:System.Collections.Generic.Dictionary%602>do. Jeśli dana przestrzeń nazw XSD zostanie znaleziona w słowniku, dopasowywana .NET Framework przestrzeń nazw jest również pobierana z słownika.  
  
 Rozważmy na przykład poniższy schemat.  
  
 [!code-xml[c_SchemaImportExport#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#10)]  
  
 Poniższy przykład używa `Namespaces` właściwości do `http://schemas.contoso.com/carSchema` mapowania przestrzeni nazw na "contoso. samochody".  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
#### <a name="adding-the-serializableattribute-generateserializable-or-the-serializable-switch"></a>Dodawanie SerializableAttribute (GenerateSerializable lub przełącznik/Serializable)  
 Odnosi się to do przełącznika **/Serializable** w `Svcutil.exe` narzędziu.  
  
 Czasami ważne jest, aby typy generowane na podstawie schematu były możliwe do użycia w aparatach serializacji środowiska uruchomieniowego .NET Framework (na <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> przykład <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> klasy i). Jest to przydatne w przypadku używania typów dla .NET Framework komunikacji zdalnej. Aby włączyć tę opcję, należy zastosować <xref:System.SerializableAttribute> atrybut do wygenerowanych typów oprócz atrybutu zwykłego. <xref:System.Runtime.Serialization.DataContractAttribute> Ten atrybut jest generowany automatycznie, jeśli `GenerateSerializable` opcja importowania jest ustawiona na `true`.  
  
 W poniższym przykładzie pokazano `Vehicle` klasy wygenerowanej `GenerateSerializable` z opcją importu ustawioną `true`na.  
  
 [!code-csharp[c_SchemaImportExport#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#4)]
 [!code-vb[c_SchemaImportExport#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#4)]  
  
#### <a name="adding-data-binding-support-enabledatabinding-or-the-enabledatabinding-switch"></a>Dodawanie obsługi powiązań danych (EnableDataBinding lub przełącznik/enableDataBinding)  
 Odnosi się to do przełącznika **/EnableDataBinding** w narzędziu Svcutil. exe.  
  
 Czasami możesz chcieć powiązać typy wygenerowane ze schematu ze składnikami graficznego interfejsu użytkownika, dzięki czemu wszystkie aktualizacje wystąpień tych typów będą automatycznie aktualizować interfejs użytkownika. Może generować typy, które <xref:System.ComponentModel.INotifyPropertyChanged> implementują interfejs w taki sposób, że każda zmiana właściwości wyzwala zdarzenie. `XsdDataContractImporter` Jeśli tworzysz typy do użycia w środowisku programowania interfejsu użytkownika klienta, które obsługuje ten interfejs (na przykład Windows Presentation Foundation (WPF)), ustaw <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A> właściwość na `true` , aby włączyć tę funkcję.  
  
 Poniższy przykład pokazuje `Vehicle` klasę wygenerowaną <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A> z zestawem do `true`.  
  
 [!code-csharp[C_SchemaImportExport#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#5)]
 [!code-vb[C_SchemaImportExport#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#5)]  
  
### <a name="import-options-choosing-collection-types"></a>Opcje importowania: Wybieranie typów kolekcji  
 Dwa specjalne wzorce w kodzie XML reprezentują kolekcje elementów: listy elementów i skojarzeń między jednym elementem a innym. Poniżej znajduje się przykład listy ciągów.  
  
 [!code-xml[C_SchemaImportExport#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#11)]  
  
 Poniżej znajduje się przykład skojarzenia między ciągiem i liczbą całkowitą (`city name` i `population`).  
  
 [!code-xml[C_SchemaImportExport#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#12)]  
  
> [!NOTE]
> Wszelkie skojarzenia można również traktować jako listę. Na przykład, można wyświetlić poprzednie skojarzenie jako listę obiektów złożonych `city` , które mają mieć dwa pola (pole String i pole typu integer). Oba wzorce mają reprezentację w schemacie XSD. Nie istnieje sposób odróżnienia między listą a skojarzeniem, dlatego takie wzorce są zawsze traktowane jako listy, chyba że Specjalna adnotacja specyficzna dla usługi WCF jest obecna w schemacie. Adnotacja wskazuje, że dany wzorzec reprezentuje skojarzenie. Aby uzyskać więcej informacji, zobacz informacje o [schemacie kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 Zwykle lista jest importowana jako kontrakt danych kolekcji, który pochodzi z listy ogólnej lub jako tablica .NET Framework, w zależności od tego, czy schemat jest zgodny ze standardowym wzorcem nazewnictwa dla kolekcji. Jest to bardziej szczegółowo opisany w części [typy kolekcji w kontraktach danych](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md). Skojarzenia są zwykle importowane jako <xref:System.Collections.Generic.Dictionary%602> kontrakt lub dane kolekcji, które pochodzą z obiektu dictionary. Rozważmy na przykład poniższy schemat.  
  
 [!code-xml[c_SchemaImportExport#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#13)]  
  
 Zostanie on zaimportowany w następujący sposób (pola są wyświetlane zamiast właściwości do czytelności).  
  
 [!code-csharp[c_SchemaImportExport#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#6)]
 [!code-vb[c_SchemaImportExport#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#6)]  
  
 Można dostosować typy kolekcji, które są generowane dla takich wzorców schematu. Na przykład, możesz chcieć generować kolekcje pochodzące z <xref:System.ComponentModel.BindingList%601> zamiast <xref:System.Collections.Generic.List%601> klasy, aby powiązać typ z polem listy i automatycznie aktualizować, gdy zawartość kolekcji zostanie zmieniona. W tym celu należy ustawić <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> Właściwość <xref:System.Runtime.Serialization.ImportOptions> klasy na listę typów kolekcji, które mają być używane (zwanych dalej typami PRZYWOŁYWANYMI). Podczas importowania kolekcji, ta lista typów kolekcji, do których się odwołuje, jest skanowana i używana jest Najlepsza kolekcja, gdy zostanie znaleziona. Skojarzenia są dopasowywane tylko do typów implementujących ogólny lub nieogólny <xref:System.Collections.IDictionary> interfejs, natomiast listy są dopasowywane do dowolnego obsługiwanego typu kolekcji.  
  
 Na przykład, jeśli <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> właściwość jest ustawiona <xref:System.ComponentModel.BindingList%601>na, `people` typ w poprzednim przykładzie jest generowany w następujący sposób.  
  
 [!code-csharp[C_SchemaImportExport#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#7)]
 [!code-vb[C_SchemaImportExport#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#7)]  
  
 Zamknięte ogólne jest uznawane za najlepsze dopasowanie. Na przykład jeśli typy `BindingList(Of Integer)` i <xref:System.Collections.ArrayList> są przesyłane do kolekcji typów, do których istnieją odwołania, wszystkie listy liczb całkowitych znalezionych w `BindingList(Of Integer)`schemacie są importowane jako. Wszystkie inne listy, na przykład a `List(Of String)`, są importowane `ArrayList`jako.  
  
 Jeśli typ implementujący interfejs generyczny `IDictionary` jest dodawany do kolekcji typów, do których istnieją odwołania, jego parametry typu muszą być w pełni otwarte lub w pełni zamknięte.  
  
 Duplikaty są niedozwolone. Na przykład nie można dodać zarówno `List(Of Integer)` , `Collection(Of Integer)` jak i a do typów, do których się odwołuje. Dzięki temu nie można ustalić, która powinna być używana w przypadku znalezienia listy liczb całkowitych w schemacie. Duplikaty będą wykrywane tylko wtedy, gdy w schemacie znajduje się typ, który ujawnia duplikaty problemu. Na przykład, Jeśli importowany schemat nie zawiera listy liczb całkowitych, może istnieć zarówno `List(Of Integer)` `Collection(Of Integer)` i w kolekcji typów, do których się odwołuje, ale żaden z nich nie będzie miał żadnego efektu.  
  
 Mechanizm typów kolekcji przywoływanych działa równie dobrze w przypadku kolekcji typów złożonych (łącznie z kolekcjami innych kolekcji), a nie tylko dla kolekcji elementów podstawowych.  
  
 Właściwość odpowiada przełącznikowi/CollectionType w narzędziu Svcutil. exe. `ReferencedCollectionTypes` Należy pamiętać, że aby odwoływać się do wielu typów kolekcji, przełącznik **/CollectionType** musi być określony wiele razy. Jeśli typ nie znajduje się w bibliotece MsCorLib. dll, jego zestaw musi być również przywoływany przy użyciu przełącznika **/Reference** .  
  
#### <a name="import-options-referencing-existing-types"></a>Opcje importowania: Odwoływanie się do istniejących typów  
 Czasami typy w schemacie odpowiadają istniejącym typom .NET Framework i nie ma potrzeby generowania tych typów od zera. (Ta sekcja ma zastosowanie tylko do typów niekolekcji. W przypadku typów kolekcji zobacz poprzednią sekcję.  
  
 Na przykład możesz mieć standardowy typ kontraktu danych "osoba" dla całej firmy, który ma być zawsze używany podczas reprezentowania osoby. Za każdym razem, gdy jakaś usługa korzysta z tego typu, a jego schemat pojawia się w metadanych usługi, można użyć istniejącego `Person` typu podczas importowania tego schematu zamiast generowania nowego dla każdej usługi.  
  
 W tym celu Przekaż listę typów .NET Framework, które mają być ponownie używane w kolekcji zwracanej przez <xref:System.Runtime.Serialization.ImportOptions.ReferencedTypes%2A> Właściwość <xref:System.Runtime.Serialization.ImportOptions> w klasie. Jeśli którykolwiek z tych typów ma nazwę kontraktu danych i przestrzeń nazw pasującą do nazwy i przestrzeni nazw typu schematu, wykonywane jest porównanie strukturalne. Jeśli określono, że typy mają zarówno zgodne nazwy, jak i zgodne struktury, istniejący typ .NET Framework jest ponownie używany zamiast generowania nowego. Jeśli tylko nazwa jest zgodna, ale nie ze strukturą, zgłaszany jest wyjątek. Należy pamiętać, że w przypadku odwołań do typów (na przykład dodawania nowych opcjonalnych elementów członkowskich danych) nie ma żadnego limitu przechowywania wersji. Struktury muszą być dokładnie zgodne.  
  
 Można dodać wiele typów z tą samą nazwą kontraktu danych i przestrzenią nazw do kolekcji typów, do których się odwołuje, o ile nie zaimportowano żadnych typów schematu z tą nazwą i przestrzenią nazw. Pozwala to łatwo dodać wszystkie typy w zestawie do kolekcji bez porzucania duplikatów dla typów, które nie występują w rzeczywistości w schemacie.  
  
 Właściwość odpowiada przełącznikowi/Reference w pewnych trybach działania narzędzia Svcutil. exe. `ReferencedTypes`  
  
> [!NOTE]
> W przypadku korzystania z programu Svcutil. exe lub (w programie Visual Studio) narzędzia **Dodaj odwołanie do usługi** wszystkie typy w bibliotece Mscorlib. dll są automatycznie przywoływane.  
  
#### <a name="import-options-importing-non-datacontract-schema-as-ixmlserializable-types"></a>Opcje importowania: Importowanie schematu innego niż DataContract jako typy IXmlSerializable  
 <xref:System.Runtime.Serialization.XsdDataContractImporter> Obsługuje ograniczony podzbiór schematu. Jeśli są obecne nieobsługiwane konstrukcje schematu (na przykład atrybuty XML), próba importu kończy się niepowodzeniem z wyjątkiem. Jednak ustawienie <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> `true` właściwości rozszerza zakres obsługiwanego schematu. Gdy jest `true` <xref:System.Runtime.Serialization.XsdDataContractImporter> ustawiona na, <xref:System.Xml.Serialization.IXmlSerializable> generuje typy, które implementują interfejs. Umożliwia to bezpośredni dostęp do reprezentacji tych typów w formacie XML.  
  
##### <a name="design-considerations"></a>Zagadnienia dotyczące projektowania  
  
- Może być trudne w obejść bezpośredniej reprezentacji XML. Rozważ użycie alternatywnego aparatu serializacji, takiego jak <xref:System.Xml.Serialization.XmlSerializer>, do pracy ze schematem, który nie jest zgodny z kontraktami danych w jednoznacznie określonym sposobie. Aby uzyskać więcej informacji, zobacz [Używanie klasy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).  
  
- Niektórych konstrukcji schematu nie można zaimportować przez <xref:System.Runtime.Serialization.XsdDataContractImporter> nawet wtedy, <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> gdy właściwość jest ustawiona na `true`. Ponownie Rozważ użycie <xref:System.Xml.Serialization.XmlSerializer> w takich przypadkach.  
  
- Dokładne konstrukcje schematu, które są obsługiwane w przypadku <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> , `true` gdy `false` jest lub są opisane w [dokumentacji schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
- Schemat wygenerowanych <xref:System.Xml.Serialization.IXmlSerializable> typów nie zachowuje wierności podczas importowania i eksportowania. Oznacza to, że eksportowanie schematu z wygenerowanych typów i importowanie jako klas nie zwraca oryginalnego schematu.  
  
 Można połączyć <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> opcję <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A> z opisaną wcześniej opcją. W przypadku typów, które muszą zostać wygenerowane jako <xref:System.Xml.Serialization.IXmlSerializable> implementacje, sprawdzanie strukturalne jest pomijane podczas korzystania z <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A> funkcji.  
  
 Opcja odnosi się do przełącznika/importXmlTypes w narzędziu Svcutil. exe. <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A>  
  
##### <a name="working-with-generated-ixmlserializable-types"></a>Praca z wygenerowanymi typami IXmlSerializable  
 Wygenerowane `IXmlSerializable` typy zawierają prywatne pole o nazwie "nodesField", które zwraca <xref:System.Xml.XmlNode> tablicę obiektów. Podczas deserializacji wystąpienia takiego typu można uzyskać dostęp do danych XML bezpośrednio za pośrednictwem tego pola przy użyciu Document Object Model XML. Podczas serializacji wystąpienia tego typu, można ustawić to pole na żądane dane XML i będzie ono serializowane.  
  
 Jest to realizowane przez `IXmlSerializable` implementację. W wygenerowanym `IXmlSerializable` typie <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> <xref:System.Runtime.Serialization.XmlSerializableServices.ReadNodes%2A> implementacja<xref:System.Runtime.Serialization.XmlSerializableServices> wywołuje metodę klasy. Metoda jest metodą pomocnika, która konwertuje kod XML dostarczony przez <xref:System.Xml.XmlReader> element do <xref:System.Xml.XmlNode> tablicy obiektów. Implementacja wykonuje przeciwieństwo i konwertuje `XmlNode` tablicę <xref:System.Xml.XmlWriter> obiektów na sekwencję wywołań. <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> Jest to realizowane za pomocą <xref:System.Runtime.Serialization.XmlSerializableServices.WriteNodes%2A> metody.  
  
 Można uruchomić proces eksportowania schematu dla wygenerowanych `IXmlSerializable` klas. Jak wspomniano wcześniej, nie zostanie pobrany oryginalny schemat z powrotem. Zamiast tego zostanie wyświetlony standardowy typ XSD "anyType", który jest symbolem wieloznacznym dla dowolnego typu XSD.  
  
 Jest to realizowane przez zastosowanie <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atrybutu do wygenerowanych `IXmlSerializable` klas i określenie metody, która wywołuje <xref:System.Runtime.Serialization.XmlSerializableServices.AddDefaultSchema%2A> metodę w celu wygenerowania typu "anyType".  
  
> [!NOTE]
> <xref:System.Runtime.Serialization.XmlSerializableServices> Typ istnieje wyłącznie do obsługi tej konkretnej funkcji. Nie jest to zalecane do użycia w żadnym innym celu.  
  
#### <a name="import-options-advanced-options"></a>Opcje importowania: Opcje zaawansowane  
 Poniżej przedstawiono zaawansowane opcje importowania:  
  
- <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A>wartość. Określ, <xref:System.CodeDom.Compiler.CodeDomProvider> który ma zostać użyty do wygenerowania kodu dla wygenerowanych klas. Mechanizm importowania próbuje uniknąć funkcji, których <xref:System.CodeDom.Compiler.CodeDomProvider> nie obsługuje. Jeśli nie <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A> jest ustawiona, pełny zestaw funkcji .NET Framework jest używany bez ograniczeń.  
  
- <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A>wartość. <xref:System.Runtime.Serialization.IDataContractSurrogate> Implementację można określić przy użyciu tej właściwości. <xref:System.Runtime.Serialization.IDataContractSurrogate> Dostosowuje proces importowania. Aby uzyskać więcej informacji, zobacz [surogaty kontraktu danych](../../../../docs/framework/wcf/extending/data-contract-surrogates.md). Domyślnie żaden Surogat nie jest używany.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- <xref:System.Runtime.Serialization.ImportOptions>
- [Odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)
- [Surogaty kontraktu danych](../../../../docs/framework/wcf/extending/data-contract-surrogates.md)
- [importowanie i eksportowanie schematu](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md)
- [Eksportowanie schematów z klas](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)
- [Odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)
