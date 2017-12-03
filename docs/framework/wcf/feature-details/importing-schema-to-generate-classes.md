---
title: Importowanie schematu w celu generowania klas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, schema import and export
- XsdDataContractImporter class
ms.assetid: b9170583-8c34-43bd-97bb-6c0c8dddeee0
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ae7ed7b1d01420c8e542d9ecce577995e927adc3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="importing-schema-to-generate-classes"></a>Importowanie schematu w celu generowania klas
Aby wygenerować klasy na podstawie schematów, której można używać z [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], użyj <xref:System.Runtime.Serialization.XsdDataContractImporter> klasy. W tym temacie opisano proces i zmian.  
  
## <a name="the-import-process"></a>Proces importowania  
 Proces importowania schematu rozpoczyna się od <xref:System.Xml.Schema.XmlSchemaSet> i tworzy <xref:System.CodeDom.CodeCompileUnit>.  
  
 `XmlSchemaSet` Jest częścią [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]tego schematu obiektu Model (model SOM) reprezentujący zestaw schematu XML definition language (XSD) schematu dokumentów. Aby utworzyć `XmlSchemaSet` obiekt z zestawu dokumentów XSD, każdy dokument do deserializacji <xref:System.Xml.Schema.XmlSchema> obiektu (przy użyciu <xref:System.Xml.Serialization.XmlSerializer>) i dodać tych obiektów na nowy `XmlSchemaSet`.  
  
 `CodeCompileUnit` Jest częścią [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]przez kod Document Object Model (CodeDOM) reprezentujący [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] kodu w sposób abstrakcyjny. Aby wygenerować kod z `CodeCompileUnit`, użyj podklasą <xref:System.CodeDom.Compiler.CodeDomProvider> klas, takich jak <xref:Microsoft.CSharp.CSharpCodeProvider> lub <xref:Microsoft.VisualBasic.VBCodeProvider> klasy.  
  
#### <a name="to-import-a-schema"></a>Aby zaimportować schematu  
  
1.  Utwórz wystąpienie <xref:System.Runtime.Serialization.XsdDataContractImporter>.  
  
2.  Opcjonalny. Przekaż `CodeCompileUnit` w konstruktorze. Typy generowane podczas importowania schematu są dodawane do tego `CodeCompileUnit` wystąpienia zamiast począwszy od pustego `CodeCompileUnit`.  
  
3.  Opcjonalny. Wywoływanie jednego z <xref:System.Runtime.Serialization.XsdDataContractImporter.CanImport%2A> metody. Metoda określa, czy dany schemat jest schematu kontraktu prawidłowe dane i mogą być importowane. `CanImport` Metoda ma tego samego przeciążeń jako `Import` (następny krok).  
  
4.  Wywoływanie jednego z przeciążone `Import` metod, na przykład <xref:System.Runtime.Serialization.XsdDataContractImporter.Import%28System.Xml.Schema.XmlSchemaSet%29> metody.  
  
     Najprostsza przeciążenia przyjmuje `XmlSchemaSet` i importuje wszystkie typy, w tym typy anonimowe, w tym zestawie schematów. Inne przeciążenia umożliwiają określenie typu XSD lub listę typów do zaimportowania (w postaci <xref:System.Xml.XmlQualifiedName> lub kolekcji `XmlQualifiedName` obiektów). W takim przypadku tylko do określonych typów są importowane. Trwa przeciążenia <xref:System.Xml.Schema.XmlSchemaElement> który importuje dany element poza `XmlSchemaSet`, oraz jego skojarzony typ (czy nie jest on anonimowego). To przeciążenie zwraca `XmlQualifiedName`, który odpowiada nazwie kontraktu danych typu wygenerowany dla tego elementu.  
  
     Wiele wywołań z `Import` wielu elementów dodawane do tej samej metody powodują `CodeCompileUnit`. Typ nie jest generowany w `CodeCompileUnit` Jeśli istnieje już istnieje. Wywołanie `Import` wiele razy w tym samym `XsdDataContractImporter` zamiast używania wielu `XsdDataContractImporter` obiektów. Jest to zalecany sposób, aby uniknąć zduplikowanych typy generowane.  
  
    > [!NOTE]
    >  W przypadku awarii podczas importowania, `CodeCompileUnit` będzie w nieprzewidywalnym stanie. Przy użyciu `CodeCompileUnit` wynikające z nieudanych importu może doprowadzić do luk w zabezpieczeniach.  
  
5.  Dostęp `CodeCompileUnit` za pośrednictwem <xref:System.Runtime.Serialization.XsdDataContractImporter.CodeCompileUnit%2A> właściwości.  
  
### <a name="import-options-customizing-the-generated-types"></a>Opcje importowania: Dostosowywanie wygenerowane typy  
 Można ustawić <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> właściwość <xref:System.Runtime.Serialization.XsdDataContractImporter> na wystąpienie <xref:System.Runtime.Serialization.ImportOptions> klasę, aby kontrolować różne aspekty procesu importowania. Liczba opcji bezpośredniego wpływania typy, które są generowane.  
  
#### <a name="controlling-the-access-level-generateinternal-or-the-internal-switch"></a>Kontrolowanie poziomu dostępu (GenerateInternal lub / wewnętrznego przełącznika)  
 Odpowiada to **/ wewnętrzny** Włącz [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 Zwykle typy publiczne zostaną wygenerowane na podstawie schematu z pól prywatnych i zgodnych właściwości elementu członkowskiego danych publicznych. Aby zamiast niego generowania typów wewnętrznych, ustaw <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A> właściwości `true`.  
  
 W poniższym przykładzie przedstawiono schematu przekształceniu wewnętrznego klasę gdy <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A> ma ustawioną wartość właściwości`true.`  
  
 [!code-csharp[c_SchemaImportExport#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#2)]
 [!code-vb[c_SchemaImportExport#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#2)]  
  
#### <a name="controlling-namespaces-namespaces-or-the-namespace-switch"></a>Kontrolowanie przestrzenie nazw (przestrzeni nazw lub w parametrze/Namespace przełącznika)  
 Odpowiada to **/Namespace** Włącz `Svcutil.exe` narzędzia.  
  
 Zwykle typy generowane na podstawie schematu są generowane w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] przestrzeni nazw z każdego obszaru nazw XSD, odpowiadającego danego [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] przestrzeni nazw zgodnie z mapowania opisanego w [odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Można dostosować to mapowanie przez <xref:System.Runtime.Serialization.ImportOptions.Namespaces%2A> właściwości <xref:System.Collections.Generic.Dictionary%602>. Jeśli danego obszaru nazw XSD zostanie znaleziony w słowniku dopasowywania [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] przestrzeń nazw również jest pobierana z słownika.  
  
 Na przykład należy wziąć pod uwagę następujące schematu.  
  
 [!code-xml[c_SchemaImportExport#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#10)]  
  
 W poniższym przykładzie użyto `Namespaces` właściwości do mapowania przestrzeni nazw "http://schemas.contoso.com/carSchema" do "Contoso.Cars".  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
#### <a name="adding-the-serializableattribute-generateserializable-or-the-serializable-switch"></a>Dodawanie atrybutu SerializableAttribute (GenerateSerializable lub / serializacji przełącznika)  
 Odpowiada to **/ serializacji** Włącz `Svcutil.exe` narzędzia.  
  
 Czasami jest ważna w przypadku typy generowane na podstawie schematu może być używany z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aparaty serializacji środowiska uruchomieniowego (na przykład <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> i <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> klasy). Jest to przydatne, gdy przy użyciu typów [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] komunikacji zdalnej. Aby włączyć tę opcję, należy zastosować <xref:System.SerializableAttribute> atrybutu wygenerowane typy oprócz zwykłej <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu. Ten atrybut jest generowane automatycznie, jeśli `GenerateSerializable` ustawiono opcję importu `true`.  
  
 W poniższym przykładzie przedstawiono `Vehicle` wygenerować za pomocą klasy `GenerateSerializable` zaimportować ustawienie `true`.  
  
 [!code-csharp[c_SchemaImportExport#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#4)]
 [!code-vb[c_SchemaImportExport#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#4)]  
  
#### <a name="adding-data-binding-support-enabledatabinding-or-the-enabledatabinding-switch"></a>Dodawanie obsługi powiązania danych (EnableDataBinding lub przełącznika /enableDataBinding)  
 Odpowiada to **/enableDataBinding** przełączania z narzędzia Svcutil.exe.  
  
 Czasami można powiązać typy generowane na podstawie schematu do składników interfejsu graficznego użytkownika, aby zaktualizowanie wystąpień tych typów są automatycznie aktualizowane interfejsu użytkownika. `XsdDataContractImporter` Można wygenerować typów, które implementują <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu w taki sposób, że zmiany właściwości wyzwala zdarzenie. Generowania typów do użycia z środowisku programowania interfejsu użytkownika klienta, który obsługuje ten interfejs (takich jak [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)]) ustaw <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A> właściwości `true` Aby włączyć tę funkcję.  
  
 W poniższym przykładzie przedstawiono `Vehicle` wygenerować za pomocą klasy <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A> ustawioną `true`.  
  
 [!code-csharp[C_SchemaImportExport#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#5)]
 [!code-vb[C_SchemaImportExport#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#5)]  
  
### <a name="import-options-choosing-collection-types"></a>Opcje import: Wybieranie typów kolekcji  
 Dwa wzorce specjalne w kodzie XML reprezentują kolekcje elementów: listę elementów i skojarzenia między jeden element. Oto przykład lista ciągów.  
  
 [!code-xml[C_SchemaImportExport#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#11)]  
  
 Poniżej przedstawiono przykład skojarzenia między string i integer (`city name` i `population`).  
  
 [!code-xml[C_SchemaImportExport#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#12)]  
  
> [!NOTE]
>  Skojarzeń można również uwzględnić listy. Na przykład można wyświetlić poprzedniego skojarzenie jako listę złożone `city` obiektów, które mają dwa pola (polem ciągu i pole Liczba całkowita). Oba wzorce ma reprezentacji w postaci w schematu XSD. Nie istnieje sposób w celu rozróżnienia listy i skojarzenia, więc tych wzorców zawsze są traktowane jako list, chyba że adnotację specjalne specyficzne dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] znajduje się w schemacie. Adnotacja wskazuje, że danego wzorca reprezentuje skojarzenia. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 Zwykle listy jest importowany jako kontraktu danych kolekcji, która pochodzi z listy ogólnej lub jako [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tablicy, w zależności od tego, czy schemat następuje standardowy wzorzec nazewnictwa dla kolekcji. To jest opisany bardziej szczegółowo w [typy kolekcji w kontraktach danych](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md). Skojarzenia są zwykle zaimportowany jako <xref:System.Collections.Generic.Dictionary%602> lub kontraktu danych kolekcji, która pochodzi z obiektu słownika. Na przykład należy wziąć pod uwagę następujące schematu.  
  
 [!code-xml[c_SchemaImportExport#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#13)]  
  
 Może to zostać zaimportowane w następujący sposób (pola są wyświetlane zamiast właściwości dla czytelności).  
  
 [!code-csharp[c_SchemaImportExport#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#6)]
 [!code-vb[c_SchemaImportExport#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#6)]  
  
 Istnieje możliwość dostosowania typy kolekcji, które są generowane dla tych wzorców schematu. Na przykład może być Generuj kolekcje pochodzące z <xref:System.ComponentModel.BindingList%601> zamiast <xref:System.Collections.Generic.List%601> klasy, aby powiązać pole listy Typ i została ona automatycznie aktualizowane podczas zmiany zawartości w kolekcji. Aby to zrobić, ustaw <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> właściwość <xref:System.Runtime.Serialization.ImportOptions> klasy do listy typów kolekcji do użycia (poniżej znane jako wskazanych typów). Podczas importowania kolekcji, ta lista wskazanych typów kolekcji jest skanowany i najlepiej pasujące kolekcja jest używana, jeśli został znaleziony. Skojarzenia są dopasowywane tylko typów, które implementują ogólnych lub nongeneric <xref:System.Collections.IDictionary> interfejsu, podczas gdy listy są dopasowywane do dowolnego typu kolekcja obsługiwanych.  
  
 Na przykład jeśli <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> właściwość jest ustawiona na <xref:System.ComponentModel.BindingList%601>, `people` typ w poprzednim przykładzie zostanie wygenerowany w następujący sposób.  
  
 [!code-csharp[C_SchemaImportExport#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#7)]
 [!code-vb[C_SchemaImportExport#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#7)]  
  
 Zamknięte rodzajowa jest traktowany jako najlepsze dopasowanie. Na przykład jeśli typy `BindingList(Of Integer)` i <xref:System.Collections.ArrayList> są przekazywane do kolekcji wskazanych typów żadnych list liczb całkowitych znaleziono w schemacie są importowane jako `BindingList(Of Integer)`. Inne listy, na przykład `List(Of String)`, są importowane jako `ArrayList`.  
  
 Jeśli typ, który implementuje ogólnego `IDictionary` interfejsu zostanie dodany do kolekcji wskazanych typów, jego parametrów typu musi być całkowicie otwarte lub całkowicie zamknięty.  
  
 Duplikaty są niedozwolone. Na przykład nie można dodać zarówno `List(Of Integer)` i `Collection(Of Integer)` do typów, do którego istnieje odwołanie. Który spowodowałoby, że nie pozwala na określenie, które mają być używane w podczas listy liczb całkowitych znajduje się w schemacie. Duplikaty zostanie wykryty tylko wtedy, gdy jest typem w schemacie, który ujawnia problem duplikaty. Na przykład, jeśli zaimportowanego schematu nie zawiera listy liczb całkowitych, jego może mieć zarówno `List(Of Integer)` i `Collection(Of Integer)` w wskazanych typów kolekcji, ale nie ma żadnego efektu.  
  
 Typy kolekcji przywoływanego mechanizmu działa równie oraz kolekcji typów złożonych (łącznie z kolekcjami innych kolekcji), a nie tylko dla kolekcji elementów podstawowych.  
  
 `ReferencedCollectionTypes` Właściwość odpowiada **/collectionType** przełączania z narzędzia SvcUtil.exe. Należy pamiętać, że można odwoływać się wiele typów kolekcji, **/collectionType** przełącznika musi być określone wiele razy. Jeśli typ nie jest w bibliotece MsCorLib.dll, jego zestaw musi także można odwoływać się przy użyciu **/reference** przełącznika.  
  
#### <a name="import-options-referencing-existing-types"></a>Opcje importowania: Odwołuje się do istniejących typów  
 Czasami odpowiadają istniejących typów w schemacie [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typów, a nie istnieje potrzeba do wygenerowania tych typów od początku. (Ta sekcja dotyczy tylko do typów noncollection. Typy kolekcji dla poprzedniej sekcji.)  
  
 Na przykład masz standardowe firmie "Osoba" typ danych kontraktu używanej zawsze gdy reprezentujący osoby. W przypadku, gdy niektóre usługi powoduje, że w metadanych usługi pojawi się użycie tego typu, a jego schematu, może zajść potrzeba ponownego użycia istniejącej `Person` wpisz podczas importowania tego schematu, zamiast generowania nowego filtru dla każdej usługi.  
  
 Aby to zrobić, należy przekazać listę [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy, które chcesz ponownie użyć do kolekcji <xref:System.Runtime.Serialization.ImportOptions.ReferencedTypes%2A> właściwość zwraca na <xref:System.Runtime.Serialization.ImportOptions> klasy. Jeśli którykolwiek z tych typów nazwie kontraktu danych i przestrzeni nazw, która jest zgodna z nazwą i przestrzeni nazw typu schematu, wykonywane jest strukturalnych porównanie. Jeśli okaże się, że typy zarówno pasujących nazw i pasujące struktury, istniejące [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typu zostanie ponownie użyty zamiast generowania nowego. Jeśli tylko nazwa taka sama, ale nie struktury, jest zgłaszany wyjątek. Należy pamiętać, że nie dodatek nie dla wersji podczas odwoływania się do typów (na przykład dodawania nowych opcjonalne elementy członkowskie danych). Struktur muszą być zgodne.  
  
 Jest prawnych, aby dodać wiele typów o tej samej nazwie kontraktu danych i przestrzeni nazw do kolekcji wskazanych typów, tak długo, jak żadnych typów schematu są importowane z tą nazwą i przestrzeni nazw. Dzięki temu można łatwo dodać wszystkich typów w zestawie do kolekcji bez obaw o duplikaty dla typów, które faktycznie nie występują w schemacie.  
  
 `ReferencedTypes` Właściwość odpowiada **/reference** przełącznika w niektórych tryby pracy narzędzia Svcutil.exe.  
  
> [!NOTE]
>  Korzystając z Svcutil.exe lub (w [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]) **Dodaj odwołanie do usługi** narzędzia, wszystkie typy w bibliotece MsCorLib.dll odwołują się automatycznie.  
  
#### <a name="import-options-importing-non-datacontract-schema-as-ixmlserializable-types"></a>Opcje importowania: Importowanie schematu DataContract inne niż jako typów IXmlSerializable  
 <xref:System.Runtime.Serialization.XsdDataContractImporter> Obsługuje ograniczonym podzbiorem schematu. W przypadku konstrukcji nieobsługiwany schemat (na przykład atrybutów XML) Próba zaimportowania kończy się niepowodzeniem z powodu wyjątku. Jednak ustawienie <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> właściwości `true` rozszerza zakres schematu obsługiwane. Jeśli wartość `true`, <xref:System.Runtime.Serialization.XsdDataContractImporter> generuje typów, które implementują <xref:System.Xml.Serialization.IXmlSerializable> interfejsu. Dzięki temu bezpośredni dostęp do reprezentacji XML tych typów.  
  
##### <a name="design-considerations"></a>Zagadnienia dotyczące projektowania  
  
-   Może być trudne do pracy bezpośrednio z lekko maszynowy reprezentacji XML. Należy wziąć pod uwagę przy użyciu aparatu serializacji alternatywnych, takich jak <xref:System.Xml.Serialization.XmlSerializer>, aby pracować ze schematem nie jest zgodne z danymi kontraktów w jednoznaczny sposób. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Przy użyciu klasy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).  
  
-   Niektóre konstrukcje schematu nie mogą być importowane przez <xref:System.Runtime.Serialization.XsdDataContractImporter> nawet wtedy, gdy <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> właściwość jest ustawiona na `true`. Ponownie, należy rozważyć użycie <xref:System.Xml.Serialization.XmlSerializer> w takich przypadkach.  
  
-   Konstrukcje dokładne schematu, które są obsługiwane zarówno po <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> jest `true` lub `false` opisanym w [odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
-   Schemat dla wygenerowany <xref:System.Xml.Serialization.IXmlSerializable> typy zachowuje wierności podczas zaimportowane i wyeksportowane. Oznacza to Eksportowanie schematu z wygenerowane typy i importowanie jako klasy nie zwraca oryginalnego schematu.  
  
 Istnieje możliwość łączenia <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> opcję z <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A> opcji opisany wcześniej. Dla typów, które mają być generowane jako <xref:System.Xml.Serialization.IXmlSerializable> implementacji, strukturalnych wyboru zostanie pominięty, przy użyciu <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A> funkcji.  
  
 <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> Opcja odnosi się do **/importXmlTypes** przełączania z narzędzia Svcutil.exe.  
  
##### <a name="working-with-generated-ixmlserializable-types"></a>Praca z typami wygenerowanego interfejsu IXmlSerializable.  
 Wygenerowany `IXmlSerializable` typów zawiera pole prywatne o nazwie "nodesField", która zwraca tablicę <xref:System.Xml.XmlNode> obiektów. Podczas deserializacji wystąpienia takiego typu, ma dostęp do danych XML bezpośrednio za pomocą tego pola przy użyciu modelu obiektu dokumentu XML. Podczas serializowania wystąpienia tego typu, w tym polu można ustawić do żądanych danych XML i będzie można serializować.  
  
 Jest to realizowane przez `IXmlSerializable` implementacji. W wygenerowanym `IXmlSerializable` typu <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> implementacja wywołuje <xref:System.Runtime.Serialization.XmlSerializableServices.ReadNodes%2A> metody <xref:System.Runtime.Serialization.XmlSerializableServices> klasy. Metoda to metoda pomocnika konwertuje XML realizowane za pośrednictwem <xref:System.Xml.XmlReader> do tablicy <xref:System.Xml.XmlNode> obiektów. <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> Implementacji nie odwrotnie i konwertuje tablicę `XmlNode` obiektów do sekwencji <xref:System.Xml.XmlWriter> wywołania. Jest to realizowane przy użyciu <xref:System.Runtime.Serialization.XmlSerializableServices.WriteNodes%2A> metody.  
  
 Istnieje możliwość uruchomienia procesu eksportowania schematu na wygenerowany `IXmlSerializable` klasy. Jak podano wcześniej nie otrzymasz oryginalnego schematu ponownie. Zamiast tego zostanie wyświetlona "anyType" standardowy typ XSD, który jest symbolem wieloznacznym dla dowolnego typu XSD.  
  
 Jest to osiągane przez zastosowanie <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atrybutu Generated `IXmlSerializable` klasy i metody określania, który odwołuje się <xref:System.Runtime.Serialization.XmlSerializableServices.AddDefaultSchema%2A> metody można wygenerować typu "anyType".  
  
> [!NOTE]
>  <xref:System.Runtime.Serialization.XmlSerializableServices> Typ istnieje wyłącznie do obsługi tej określonej funkcji. Nie zaleca się do użytku dla innych celów.  
  
#### <a name="import-options-advanced-options"></a>Opcje importowania: Opcje zaawansowane  
 Poniżej są zaawansowane opcje importowania:  
  
-   <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A>Właściwość. Określ <xref:System.CodeDom.Compiler.CodeDomProvider> używany do generowania kodu dla wygenerowanego klas. Funkcje prób mechanizmu importu, aby uniknąć <xref:System.CodeDom.Compiler.CodeDomProvider> nie obsługuje. Jeśli <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A> nie jest ustawiona, pełny zestaw [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] funkcji jest używana bez ograniczeń.  
  
-   <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A>Właściwość. <xref:System.Runtime.Serialization.IDataContractSurrogate> Za pomocą tej właściwości można określić implementacji. <xref:System.Runtime.Serialization.IDataContractSurrogate> Dostosowuje proces importowania. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Surogatów kontraktu danych](../../../../docs/framework/wcf/extending/data-contract-surrogates.md). Domyślnie surogat nie jest używany.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.XsdDataContractImporter>  
 <xref:System.Runtime.Serialization.XsdDataContractExporter>  
 <xref:System.Runtime.Serialization.ImportOptions>  
 [Odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)  
 [Surogaty kontraktu danych](../../../../docs/framework/wcf/extending/data-contract-surrogates.md)  
 [Importowanie i eksportowanie schematu](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md)  
 [Eksportowanie schematów z klas](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)  
 [Odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)
