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
ms.openlocfilehash: 68890a5d86d2781e3c8079c86e941144e3796ea6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228591"
---
# <a name="importing-schema-to-generate-classes"></a>Importowanie schematu w celu generowania klas
Aby wygenerować klasy schematów, które można używać za pomocą programu Windows Communication Foundation (WCF), należy użyć <xref:System.Runtime.Serialization.XsdDataContractImporter> klasy. W tym temacie opisano proces i zmian.  
  
## <a name="the-import-process"></a>Proces importowania
 Proces importowania schematu, który rozpoczyna się od <xref:System.Xml.Schema.XmlSchemaSet> i tworzy <xref:System.CodeDom.CodeCompileUnit>.  
  
 `XmlSchemaSet` Jest częścią [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]firmy schematu Object Model (model SOM) reprezentujący zestaw dokumentów schematu języka (XSD) definicji schematu XML. Aby utworzyć `XmlSchemaSet` obiektów z zestawu dokumentów XSD, każdy dokument do deserializacji <xref:System.Xml.Schema.XmlSchema> obiekt (przy użyciu <xref:System.Xml.Serialization.XmlSerializer>) i Dodaj te obiekty do nowego `XmlSchemaSet`.  
  
 `CodeCompileUnit` Jest częścią [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]firmy kodu Document Object Model (CodeDOM) reprezentujący [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] kodu w sposób abstrakcyjne. Aby wygenerować kod z `CodeCompileUnit`, użyj podklasą <xref:System.CodeDom.Compiler.CodeDomProvider> klasy, takie jak <xref:Microsoft.CSharp.CSharpCodeProvider> lub <xref:Microsoft.VisualBasic.VBCodeProvider> klasy.  
  
### <a name="to-import-a-schema"></a>Aby zaimportować schematu  
  
1. Utwórz wystąpienie obiektu <xref:System.Runtime.Serialization.XsdDataContractImporter>.  
  
2. Opcjonalna. Przekaż `CodeCompileUnit` w konstruktorze. Typy generowane podczas importowania schematu są dodawane do tego `CodeCompileUnit` wystąpienie zamiast począwszy od pustego `CodeCompileUnit`.  
  
3. Opcjonalna. Wywołanie jednej z <xref:System.Runtime.Serialization.XsdDataContractImporter.CanImport%2A> metody. Metoda określa, czy dany schemat jest schematu kontraktu prawidłowych danych i mogą być importowane. `CanImport` Metoda ma tego samego przeciążenia jako `Import` (następny krok).  
  
4. Wywołanie jednej z przeciążonych `Import` metody, na przykład <xref:System.Runtime.Serialization.XsdDataContractImporter.Import%28System.Xml.Schema.XmlSchemaSet%29> metody.  
  
     Najprostsza przeciążenia przyjmuje `XmlSchemaSet` , a następnie importuje wszystkie typy, w tym typy anonimowe, w tym zestawie schematów. Inne przeciążenia pozwalają na określenie typu XSD lub Podaj listę typów, aby zaimportować (w postaci <xref:System.Xml.XmlQualifiedName> lub kolekcję `XmlQualifiedName` obiektów). W tym przypadku są importowane tylko do określonych typów. Trwa przeciążenia <xref:System.Xml.Schema.XmlSchemaElement> który importuje konkretnego elementu z `XmlSchemaSet`, a także jego skojarzony typ (czy jest anonimowa lub nie). Tego przeciążenia zwraca `XmlQualifiedName`, która reprezentuje nazwę kontraktu danych typu wygenerowanego dla tego elementu.  
  
     Wiele wywołań z `Import` metody powodują wielu elementów, które są dodawane do tej samej `CodeCompileUnit`. Typ nie jest generowany w `CodeCompileUnit` Jeśli istnieje już istnieje. Wywołaj `Import` wiele razy w tym samym `XsdDataContractImporter` zamiast używania wielu `XsdDataContractImporter` obiektów. To jest zalecanym sposobem uniknięcia typy zduplikowanych generowany.  
  
    > [!NOTE]
    > Jeśli wystąpi awaria podczas importowania, `CodeCompileUnit` będą znajdować się w nieprzewidywalnym stanie. Za pomocą `CodeCompileUnit` wynikające z nieudanych import może doprowadzić do luk w zabezpieczeniach.  
  
5. Dostęp do `CodeCompileUnit` za pośrednictwem <xref:System.Runtime.Serialization.XsdDataContractImporter.CodeCompileUnit%2A> właściwości.  
  
### <a name="import-options-customizing-the-generated-types"></a>Opcje importowania: Dostosowywanie wygenerowane typy  
 Możesz ustawić <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> właściwość <xref:System.Runtime.Serialization.XsdDataContractImporter> do wystąpienia <xref:System.Runtime.Serialization.ImportOptions> klasy, aby kontrolować różne aspekty procesu importowania. Liczba opcji bezpośrednio wpływają na typy, które są generowane.  
  
#### <a name="controlling-the-access-level-generateinternal-or-the-internal-switch"></a>Kontrolowanie poziomu dostępu (GenerateInternal lub / wewnętrzny Przełącz)  
 Odpowiada to **/ wewnętrzny** Włącz [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 Zwykle typy publiczne są generowane na podstawie schematu, za pomocą pola prywatne i zgodne właściwości elementów członkowskich danych publicznych. Aby wygenerować typy wewnętrzne zamiast niego, ustaw <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A> właściwość `true`.  
  
 Poniższy przykład przedstawia schematu, przekształcane na wewnętrzną klasę gdy <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A> właściwość jest ustawiona na `true.`  
  
 [!code-csharp[c_SchemaImportExport#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#2)]
 [!code-vb[c_SchemaImportExport#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#2)]  
  
#### <a name="controlling-namespaces-namespaces-or-the-namespace-switch"></a>Kontrolowanie przestrzenie nazw (przestrzeni nazw lub/namespace, przełącz)  
 Odpowiada to **/Namespace** Włącz `Svcutil.exe` narzędzia.  
  
 Zwykle typy generowane na podstawie schematu są generowane w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] przestrzeni nazw, z każdego obszaru nazw XSD, odpowiadający określonego [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] przestrzeni nazw zgodnie z mapowania z opisem w temacie [odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Można dostosować to mapowanie przez <xref:System.Runtime.Serialization.ImportOptions.Namespaces%2A> właściwość <xref:System.Collections.Generic.Dictionary%602>. Jeśli danego obszaru nazw XSD zostanie znaleziony w słowniku dopasowywania [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] przestrzeń nazw również jest pobierana z słownika.  
  
 Na przykład należy wziąć pod uwagę poniższe schemat.  
  
 [!code-xml[c_SchemaImportExport#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#10)]  
  
 W poniższym przykładzie użyto `Namespaces` właściwości, aby zamapować `http://schemas.contoso.com/carSchema` przestrzeń nazw "Contoso.Cars".  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
#### <a name="adding-the-serializableattribute-generateserializable-or-the-serializable-switch"></a>Dodawanie atrybutu SerializableAttribute (GenerateSerializable lub / serializacji Przełącz)  
 Odpowiada to **/ serializacji** Włącz `Svcutil.exe` narzędzia.  
  
 Czasem ważne jest, aby typy generowane na podstawie schematu może być używany z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aparatów serializacji w czasie wykonywania (na przykład <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> i <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> klasy). Jest to przydatne, gdy przy użyciu typów dla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] komunikacji zdalnej. Aby je włączyć, należy najpierw zastosować <xref:System.SerializableAttribute> atrybutu wygenerowane typy oprócz zwykłych <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu. Ten atrybut jest generowana automatycznie, jeśli `GenerateSerializable` ustawiono opcję importowania `true`.  
  
 W poniższym przykładzie przedstawiono `Vehicle` klasy wygenerowanej z `GenerateSerializable` opcja równa importu `true`.  
  
 [!code-csharp[c_SchemaImportExport#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#4)]
 [!code-vb[c_SchemaImportExport#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#4)]  
  
#### <a name="adding-data-binding-support-enabledatabinding-or-the-enabledatabinding-switch"></a>Dodanie obsługi powiązanie danych (EnableDataBinding lub przełącznika /enableDataBinding)  
 Odpowiada to **/enableDataBinding** Włącz narzędzia Svcutil.exe.  
  
 Czasami można powiązać typy generowane na podstawie schematu do składników interfejsu graficznego użytkownika, aby wszelkich aktualizacji wystąpienia tych typów zostanie automatycznie zaktualizowany interfejs użytkownika. `XsdDataContractImporter` Może wygenerować typy, które implementują <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu w taki sposób, że każda zmiana właściwości wyzwala zdarzenie. Generowania typów do użycia z usługą środowisku programowania interfejsu użytkownika klienta, który obsługuje ten interfejs (takich jak Windows Presentation Foundation (WPF)), ustaw <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A> właściwość `true` Aby włączyć tę funkcję.  
  
 W poniższym przykładzie przedstawiono `Vehicle` klasy wygenerowanej z <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A> równa `true`.  
  
 [!code-csharp[C_SchemaImportExport#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#5)]
 [!code-vb[C_SchemaImportExport#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#5)]  
  
### <a name="import-options-choosing-collection-types"></a>Opcje importowania: Wybieranie typów kolekcji  
 Dwa wzorce specjalne w kodzie XML reprezentują kolekcje elementów: listy elementów i skojarzenia elementu jednego i drugiego. Oto przykład listy ciągów.  
  
 [!code-xml[C_SchemaImportExport#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#11)]  
  
 Oto przykład skojarzenie między ciągu i liczby całkowitej (`city name` i `population`).  
  
 [!code-xml[C_SchemaImportExport#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#12)]  
  
> [!NOTE]
>  Skojarzenia można też je traktować jako listę. Na przykład, można wyświetlić poprzedni skojarzenie jako lista złożone `city` obiektów, które mają dwa pola (pole ciągu i pola Liczba całkowita). Oba wzorce ma reprezentacji w schematu XSD. Nie ma możliwości do rozróżnienia między listy i skojarzenia, dzięki czemu takie wzorce są zawsze traktowane jako list, chyba że specjalne adnotacji specyficzne dla usługi WCF jest obecny w schemacie. Adnotacja wskazuje, że danego wzorca reprezentuje skojarzenia. Aby uzyskać więcej informacji, zobacz [odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 Zwykle listy jest importowany jako kontraktu danych kolekcji, która wynika z listy ogólnej lub jako [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tablicy, w zależności od tego, czy schemat następuje standardowego wzorca nazewnictwa dla kolekcji. Jest to opisane bardziej szczegółowo w [typy kolekcji w kontraktach danych](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md). Skojarzenia są normalnie zaimportowane jako <xref:System.Collections.Generic.Dictionary%602> lub kontraktu danych kolekcji, która wynika z obiekt słownika. Na przykład należy wziąć pod uwagę poniższe schemat.  
  
 [!code-xml[c_SchemaImportExport#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#13)]  
  
 To zostaną zaimportowane, w następujący sposób (pola są wyświetlane zamiast właściwości, aby zwiększyć czytelność).  
  
 [!code-csharp[c_SchemaImportExport#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#6)]
 [!code-vb[c_SchemaImportExport#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#6)]  
  
 Istnieje możliwość dostosować typy kolekcji, które są generowane dla wzorców takich schematu. Na przykład warto wygenerować kolekcji pochodząca od <xref:System.ComponentModel.BindingList%601> zamiast <xref:System.Collections.Generic.List%601> klasy w celu powiązania typu z pola listy i jest automatycznie aktualizowane po zmianie wartości w kolekcji. Aby to zrobić, należy ustawić <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> właściwość <xref:System.Runtime.Serialization.ImportOptions> klasy do listy typów kolekcji do użycia (dalej nazywanej przywoływane typy). Podczas importowania dowolnej kolekcji, ta lista wskazanych typów kolekcji jest skanowany i najlepiej pasujące kolekcja jest używana, jeśli został znaleziony. Skojarzenia będą dopasowywane tylko typy, które implementują ogólnego lub nongeneric <xref:System.Collections.IDictionary> interfejsu, podczas gdy list są dopasowywane do dowolnego typu kolekcji obsługiwanych.  
  
 Na przykład jeśli <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> właściwość jest ustawiona na <xref:System.ComponentModel.BindingList%601>, `people` typu w powyższym przykładzie jest generowany w następujący sposób.  
  
 [!code-csharp[C_SchemaImportExport#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#7)]
 [!code-vb[C_SchemaImportExport#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#7)]  
  
 Zamknięte ogólnego jest traktowany jako najlepsze dopasowanie. Na przykład jeśli typy `BindingList(Of Integer)` i <xref:System.Collections.ArrayList> są przekazywane do kolekcji typów, wszystkie listy liczb całkowitych, znaleziono w schemacie są importowane jako `BindingList(Of Integer)`. Inne listy, na przykład `List(Of String)`, są importowane jako `ArrayList`.  
  
 Jeśli typ, który implementuje ogólnego `IDictionary` interfejs jest dodawany do kolekcji typów, jego parametrów typu musi być całkowicie otwarte lub zamknięte w pełni.  
  
 Duplikaty są niedozwolone. Na przykład nie można dodać oba `List(Of Integer)` i `Collection(Of Integer)` dla typów odwołania. Które spowodowałoby, że niemożliwe do należy określić, które powinny być używane, gdy znajduje się na liście liczb całkowitych w schemacie. Duplikaty zostanie wykryty, tylko wtedy, gdy typem w schemacie, który udostępnia problem duplikaty. Na przykład, jeśli zaimportowanego schematu nie zawiera listy liczb całkowitych, może on być mieć zarówno `List(Of Integer)` i `Collection(Of Integer)` w wskazanych typów kolekcji, ale nie będzie mieć żadnego efektu.  
  
 Typy kolekcji do którego istnieje odwołanie, mechanizm działa równie dobrze dla kolekcji typów złożonych (w tym kolekcji innych kolekcji), a nie tylko dla kolekcji elementów podstawowych.  
  
 `ReferencedCollectionTypes` Właściwość odpowiada **/collectionType** Włącz narzędzia SvcUtil.exe. Należy pamiętać, że można odwoływać się do wielu typów kolekcji, **/collectionType** przełącznik musi zostać określony wiele razy. Jeśli typ nie ma MsCorLib.dll, jej zestawu musi także odwoływać się za pomocą **/reference** przełącznika.  
  
#### <a name="import-options-referencing-existing-types"></a>Opcje importowania: Odwoływanie się do istniejących typów  
 Od czasu do czasu typów w schemacie odnoszą się do istniejącej [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typów, i nie ma potrzeby do wygenerowania tych typów od podstaw. (Ta sekcja dotyczy tylko typów noncollection. Aby typy kolekcji zobacz poprzednią sekcję).  
  
 Na przykład masz standardowa całej firmy "Person" Typ kontraktu danych, który ma być zawsze używane podczas reprezentująca osobę. W przypadku, gdy niektóre service umożliwia korzystanie z tego typu i jego schematu, który pojawia się w metadanych usługi, może zajść potrzeba ponownego użycia istniejącej `Person` wpisz podczas importowania tego schematu, zamiast generować nową dla każdej usługi.  
  
 Aby to zrobić, należy przekazać listę [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy, które chcesz użyć ponownie do kolekcji <xref:System.Runtime.Serialization.ImportOptions.ReferencedTypes%2A> właściwość zwraca na <xref:System.Runtime.Serialization.ImportOptions> klasy. Jeśli którykolwiek z tych typów nazwie kontraktu danych i przestrzeni nazw, która jest zgodna z nazwą i przestrzeni nazw typu schematu, jest wykonywane porównywania strukturalnego. Jeśli okaże się, że typy mają pasujące nazwy i struktury zgodne, istniejące [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typu zostanie ponownie użyty zamiast generować nową. Jeśli tylko nazwa taka sama, ale nie struktury, jest zgłaszany wyjątek. Należy pamiętać, że dodatek nie pod kątem przechowywania wersji podczas odwoływania się do typów (na przykład dodawania nowych opcjonalnymi danymi członków). Struktury musi dokładnie pasować.  
  
 Jest legalne, aby dodać wiele typów o tej samej nazwie kontraktu danych i przestrzeni nazw do kolekcji typów, tak długo, jak żadnych typów schematu są importowane z tą nazwą i przestrzeni nazw. Dzięki temu można łatwo dodać wszystkich typów w zestawie do kolekcji bez martwienia się o duplikaty dla typów, które faktycznie nie występują w schemacie.  
  
 `ReferencedTypes` Właściwość odpowiada **/reference** przełącznika w niektórych tryby działania narzędzia Svcutil.exe.  
  
> [!NOTE]
>  Korzystając z Svcutil.exe lub (w programie Visual Studio) **Dodaj odwołanie do usługi** narzędzia, wszystkie typy w MsCorLib.dll są automatycznie dołączane.  
  
#### <a name="import-options-importing-non-datacontract-schema-as-ixmlserializable-types"></a>Opcje importowania: Importowanie schematu DataContract inne niż jako typów IXmlSerializable  
 <xref:System.Runtime.Serialization.XsdDataContractImporter> Obsługuje podzbiór ograniczony schemat. W przypadku konstrukcji schematu nieobsługiwaną (na przykład atrybutów XML) próba import zakończy się niepowodzeniem z powodu wyjątku. Jednak ustawienie <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> właściwość `true` rozszerza zakres schematu obsługiwane. Po ustawieniu `true`, <xref:System.Runtime.Serialization.XsdDataContractImporter> generuje typy, które implementują <xref:System.Xml.Serialization.IXmlSerializable> interfejsu. Dzięki temu bezpośredni dostęp do tych typów reprezentację XML.  
  
##### <a name="design-considerations"></a>Zagadnienia dotyczące projektowania  
  
-   Może być trudne do pracy z słabo typizowaną reprezentację XML bezpośrednio. Należy wziąć pod uwagę przy użyciu mechanizm serializacji alternatywnych, takich jak <xref:System.Xml.Serialization.XmlSerializer>, aby pracować ze schematem nie jest zgodna z danymi kontraktów w silnie typizowany sposób. Aby uzyskać więcej informacji, zobacz [przy użyciu klasy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).  
  
-   Nie można zaimportować niektórych konstrukcji schematu przez <xref:System.Runtime.Serialization.XsdDataContractImporter> nawet wtedy, gdy <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> właściwość jest ustawiona na `true`. Ponownie, należy rozważyć użycie <xref:System.Xml.Serialization.XmlSerializer> w takich przypadkach.  
  
-   Konstrukcji dokładnie schematu, które są obsługiwane zarówno po <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> jest `true` lub `false` są opisane w [odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
-   Wygenerowany schemat <xref:System.Xml.Serialization.IXmlSerializable> typy zachowuje wierności po zaimportowaniu i wyeksportowane. Oznacza to, że Eksportowanie schematu z wygenerowane typy i importowanie jako klasy nie zwraca oryginalnym schematem.  
  
 Można połączyć <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> z opcją <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A> opisanej wcześniej. Dla typów, które mają zostać wygenerowane jako <xref:System.Xml.Serialization.IXmlSerializable> implementacji, strukturalnych wyboru zostanie pominięta, gdy za pomocą <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A> funkcji.  
  
 <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> Opcja odnosi się do **/importXmlTypes** Włącz narzędzia Svcutil.exe.  
  
##### <a name="working-with-generated-ixmlserializable-types"></a>Praca z typami IXmlSerializable wygenerowany  
 Wygenerowany `IXmlSerializable` typy zawierać pola prywatnego, o nazwie "nodesField", która zwraca tablicę <xref:System.Xml.XmlNode> obiektów. Podczas deserializacji wystąpienia taki typ, mają dostęp do danych XML bezpośrednio w ramach tego pola, za pomocą XML Document Object Model. Podczas serializacji wystąpienia tego typu, można ustawić tego pola do żądanej dane XML i będzie serializowana.  
  
 Jest to realizowane za pośrednictwem `IXmlSerializable` implementacji. W wygenerowanym `IXmlSerializable` typu <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> implementacja wywołuje <xref:System.Runtime.Serialization.XmlSerializableServices.ReadNodes%2A> metody <xref:System.Runtime.Serialization.XmlSerializableServices> klasy. Metoda jest metodą pomocnika, która konwertuje XML realizowane za pośrednictwem <xref:System.Xml.XmlReader> tablicę <xref:System.Xml.XmlNode> obiektów. <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> Implementacja ma odwrotne i konwertuje tablicę `XmlNode` obiektów z sekwencji <xref:System.Xml.XmlWriter> wywołania. Jest to realizowane przy użyciu <xref:System.Runtime.Serialization.XmlSerializableServices.WriteNodes%2A> metody.  
  
 Istnieje możliwość uruchomienia procesu eksportowania schematu w wygenerowanym `IXmlSerializable` klasy. Podaną wcześniej nie otrzymasz oryginalnym schematem ponownie. Zamiast tego zostanie wyświetlony "anyType" Standardowa typ XSD, czyli symbol wieloznaczny dla dowolnego typu XSD.  
  
 Jest to osiągane przez zastosowanie <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atrybutu Generated `IXmlSerializable` klasy i określanie metody wywołująca <xref:System.Runtime.Serialization.XmlSerializableServices.AddDefaultSchema%2A> metodę w celu wygenerowania typu "anyType".  
  
> [!NOTE]
>  <xref:System.Runtime.Serialization.XmlSerializableServices> Typ istnieje wyłącznie do obsługi tej określonej funkcji. Nie jest zalecane do użytku w żadnym innym celu.  
  
#### <a name="import-options-advanced-options"></a>Opcje importowania: Opcje zaawansowane  
 Poniżej są zaawansowane opcje importowania:  
  
-   <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A> Właściwość. Określ <xref:System.CodeDom.Compiler.CodeDomProvider> służące do generowania kodu dla wygenerowanej klasy. Funkcje prób mechanizm importu, aby uniknąć <xref:System.CodeDom.Compiler.CodeDomProvider> nie obsługuje. Jeśli <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A> nie jest ustawiona, pełny zestaw [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] funkcji jest używany bez żadnych ograniczeń.  
  
-   <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A> Właściwość. <xref:System.Runtime.Serialization.IDataContractSurrogate> Za pomocą tej właściwości można określić implementacji. <xref:System.Runtime.Serialization.IDataContractSurrogate> Dostosowuje proces importowania. Aby uzyskać więcej informacji, zobacz [surogaty kontraktu danych](../../../../docs/framework/wcf/extending/data-contract-surrogates.md). Domyślnie jest używany nie zastępczy.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- <xref:System.Runtime.Serialization.ImportOptions>
- [Odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)
- [Surogaty kontraktu danych](../../../../docs/framework/wcf/extending/data-contract-surrogates.md)
- [Importowanie i eksportowanie schematu](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md)
- [Eksportowanie schematów z klas](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)
- [Odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)
