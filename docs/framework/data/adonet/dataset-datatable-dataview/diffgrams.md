---
title: DataSets
ms.date: 03/30/2017
ms.assetid: 037f3991-7bbc-424b-b52e-8b03585d3e34
ms.openlocfilehash: fd452efff2a26b66c06a7762b215df140047286d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402050"
---
# <a name="diffgrams"></a>DataSets
Format DiffGram jest w formacie XML, który identyfikuje bieżąca i oryginalna wersja elementów danych. <xref:System.Data.DataSet> Używa formatu w formacie DiffGram do ładowania i utrzymują się jego zawartość i do wykonywania serializacji jego zawartość dla transportu połączenia sieciowego. Gdy <xref:System.Data.DataSet> są zapisywane jako element w formacie DiffGram, wypełnia ją w formacie DiffGram wszystkie niezbędne informacje dokładnie odtworzyć zawartość, jednak nie schematu z <xref:System.Data.DataSet>, w tym wartości kolumn z obu **oryginalnego** i **bieżącego** wersji wierszy, informacje o błędzie wiersza i kolejności wierszy.  
  
 Jeśli przesyłanie i pobieranie <xref:System.Data.DataSet> z usługi sieci Web XML niejawnie jest używany format w formacie DiffGram. Ponadto podczas ładowania zawartości <xref:System.Data.DataSet> z XML przy użyciu **ReadXml** metodę, lub podczas zapisywania zawartości <xref:System.Data.DataSet> XML przy użyciu **WriteXml** metody, można określić Czy można odczytać lub zapisywane jako element w formacie DiffGram zawartości. Aby uzyskać więcej informacji, zobacz [Ładowanie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) i [zapisywanie zawartości elementu DataSet jako danych XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 Gdy format w formacie DiffGram jest używany głównie w programie .NET Framework jako format serializacji dla zawartości <xref:System.Data.DataSet>, można również użyć DataSets do modyfikacji danych w tabelach w bazie danych programu Microsoft SQL Server.  
  
 Format Diffgram jest generowany przez zapisywanie zawartości wszystkich tabel do  **\<w formacie diffgram >** elementu.  
  
### <a name="to-generate-a-diffgram"></a>Aby wygenerować obiektu Diffgram  
  
1.  Wygeneruj listę tabel głównych (czyli tabele bez żadnych nadrzędnego).  
  
2.  Dla każdej tabeli i jego elementy podrzędne na liście zapisać bieżącą wersję wszystkich wierszy w pierwszej sekcji w formacie Diffgram.  
  
3.  Dla każdej tabeli w <xref:System.Data.DataSet>, zapisać oryginalną wersję wszystkich wierszy, jeśli istnieją w  **\<przed >** części w formacie Diffgram.  
  
4.  Dla wierszy, które mają błędy, pisanie zawartości w błąd  **\<błędy >** części w formacie Diffgram.  
  
 Format Diffgram są przetwarzane w kolejności od początku pliku XML na końcu.  
  
### <a name="to-process-a-diffgram"></a>Do przetworzenia w formacie Diffgram  
  
1.  Proces w pierwszej sekcji Format Diffgram, która zawiera bieżącą wersję wierszy.  
  
2.  Przetwarzanie drugi lub  **\<przed >** sekcji, który zawiera oryginalną wersję wiersz zmodyfikowany i usunięte wiersze.  
  
    > [!NOTE]
    >  Jeśli wiersz jest oznaczony jako usunięty, operacja usuwania może usunąć wiersza elementy podrzędne, w zależności od `Cascade` właściwości bieżącego <xref:System.Data.DataSet>.  
  
3.  Proces  **\<błędy >** sekcji. Ustaw informacje o błędzie dla określonego wiersza i kolumny dla każdego elementu w tej sekcji.  
  
> [!NOTE]
>  Jeśli ustawisz <xref:System.Data.XmlWriteMode> na format Diffgram, zawartość elementu docelowego <xref:System.Data.DataSet> a oryginalny wskaźnik <xref:System.Data.DataSet> mogą się różnić.  
  
## <a name="diffgram-format"></a>Format w formacie DiffGram  
 Format w formacie DiffGram jest podzielony na trzy sekcje: bieżące dane, oryginalnym (lub "before") danych i sekcję błędy, jak pokazano w poniższym przykładzie.  
  
```xml  
<?xml version="1.0"?>  
<diffgr:diffgram   
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"  
         xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1"  
         xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  
   <DataInstance>  
   </DataInstance>  
  
  <diffgr:before>  
  </diffgr:before>  
  
  <diffgr:errors>  
  </diffgr:errors>  
</diffgr:diffgram>  
```  
  
 Format w formacie DiffGram składa się z następujących bloków danych:  
  
 **\<**  ***DataInstance***  **>**  
 Nazwa tego elementu ***DataInstance***, zostaną użyte do celów wyjaśnienie w tej dokumentacji. A ***DataInstance*** element reprezentuje <xref:System.Data.DataSet> lub wiersza <xref:System.Data.DataTable>. Zamiast *DataInstance*, element może zawierać nazwy <xref:System.Data.DataSet> lub <xref:System.Data.DataTable>. Ten blok format w formacie DiffGram zawiera bieżące dane, czy został zmodyfikowany lub nie. Element lub wiersza, który został zmodyfikowany, jest identyfikowany za pomocą **diffgr:hasChanges** adnotacji.  
  
 **\<diffgr: przed >**  
 Ten blok format w formacie DiffGram zawiera oryginalną wersję wiersza. Elementy w tym bloku są dopasowywane do elementów w ***DataInstance*** zablokowane, używając **diffgr:id** adnotacji.  
  
 **\<diffgr:errors >**  
 Ten blok format w formacie DiffGram zawiera informacje o błędzie dla danego wiersza w ***DataInstance*** bloku. Elementy w tym bloku są dopasowywane do elementów w ***DataInstance*** zablokowane, używając **diffgr:id** adnotacji.  
  
## <a name="diffgram-annotations"></a>Adnotacje w formacie DiffGram  
 DataSets korzystanie z adnotacji kilka powiązanie elementów z różnych bloków w formacie DiffGram, reprezentujących innego wiersza wersji lub informacje o błędzie w <xref:System.Data.DataSet>.  
  
 W poniższej tabeli opisano adnotacje w formacie DiffGram, które są zdefiniowane w przestrzeni nazw w formacie DiffGram **urn: schemas-microsoft-com: XML-format diffgram — v1**.  
  
|Adnotacja|Opis|  
|----------------|-----------------|  
|**id**|Używany do pary elementów w  **\<diffgr: przed >** i  **\<diffgr:errors >** bloków do elementów w **\<** ***DataInstance*** **>** bloku. Wartości z **diffgr:id** adnotacji znajdują się w formularzu *[Nazwa_tabeli] [RowIdentifier]*. Na przykład: `<Customers diffgr:id="Customers1">`.|  
|**parentId**|Identyfikuje element, który z **\<** ***DataInstance*** **>** bloku jest elementem nadrzędnym bieżącego elementu. Wartości z **diffgr:parentId** adnotacji znajdują się w formularzu *[Nazwa_tabeli] [RowIdentifier]*. Na przykład: `<Orders diffgr:parentId="Customers1">`.|  
|**haschanges —**|Identyfikuje wiersz w **\<** ***DataInstance*** **>** block zmodyfikowana. **Haschanges —** adnotacji może mieć jedną z dwóch wartości:<br /><br /> **Wstawiono**<br /> Identyfikuje **dodano** wiersza.<br /><br /> **Zmodyfikowane**<br /> Identyfikuje **zmodyfikowane** wiersza, który zawiera **oryginalnego** wersji wierszy w  **\<diffgr: przed >** bloku. Należy pamiętać, że **usunięte** wiersze będą mieć **oryginalnego** wersji wierszy w  **\<diffgr: przed >** blok, ale nie będzie można żaden element adnotacjami w **\<** ***DataInstance*** **>** bloku.|  
|**hasErrors**|Identyfikuje wiersz w **\<** ***DataInstance*** **>** blokowania z **RowError**. Błąd elementu jest umieszczany w  **\<diffgr:errors >** bloku.|  
|**Błąd**|Zawiera tekst **RowError** dla określonego elementu w  **\<diffgr:errors >** bloku.|  
  
 <xref:System.Data.DataSet> Obejmuje dodatkowe adnotacje podczas odczytu lub zapisu jego zawartość jako element w formacie DiffGram. W poniższej tabeli opisano te dodatkowe adnotacje, które są zdefiniowane w przestrzeni nazw **urn: schemas-microsoft-com: XML-msdata**.  
  
|Adnotacja|Opis|  
|----------------|-----------------|  
|**RowOrder**|Zachowuje kolejności wierszy oryginalnych danych i identyfikuje indeks wiersza, w szczególności <xref:System.Data.DataTable>.|  
|**Ukryte**|Identyfikuje kolumny jako posiadające **ColumnMapping** właściwością **MappingType.Hidden**. Ten atrybut jest zapisywany w formacie **msdata: ukryte** *[NazwaKolumny]*= "*wartość*". Na przykład: `<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">`.<br /><br /> Należy pamiętać, że ukryte kolumny są zapisywane tylko jako atrybut format DiffGram jeśli zawierają one dane. W przeciwnym razie są ignorowane.|  
  
## <a name="sample-diffgram"></a>Przykładowy format DiffGram  
 Poniżej przedstawiono przykład formatu w formacie DiffGram. Ten przykład przedstawia wynik aktualizacji do wiersza w tabeli, aby zmiany zostały zatwierdzone. Wiersz z CustomerID "ALFKI" ma został zmodyfikowany, ale nie zaktualizowano. Co w efekcie występuje **bieżącego** wiersz z **diffgr:id** z "Customers1" w **\<** ***DataInstance*** **>** bloku, a **oryginalnego** wiersz z **diffgr:id** z "Customers1" w  **\<diffgr: przed >** bloku. Zawiera wiersz z CustomerID "ANATR" **RowError**, dlatego jest oznaczona za pomocą `diffgr:hasErrors="true"` i powiązane elementu w  **\<diffgr:errors >** bloku.  
  
```xml  
<diffgr:diffgram xmlns:msdata="urn:schemas-microsoft-com:xml-msdata" xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
  <CustomerDataSet>  
    <Customers diffgr:id="Customers1" msdata:rowOrder="0" diffgr:hasChanges="modified">  
      <CustomerID>ALFKI</CustomerID>  
      <CompanyName>New Company</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers2" msdata:rowOrder="1" diffgram:hasErrors="true">  
      <CustomerID>ANATR</CustomerID>  
      <CompanyName>Ana Trujillo Emparedados y Helados</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers3" msdata:rowOrder="2">  
      <CustomerID>ANTON</CustomerID>  
      <CompanyName>Antonio Moreno Taquera</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers4" msdata:rowOrder="3">  
      <CustomerID>AROUT</CustomerID>  
      <CompanyName>Around the Horn</CompanyName>  
    </Customers>  
  </CustomerDataSet>  
  <diffgr:before>  
    <Customers diffgr:id="Customers1" msdata:rowOrder="0">  
      <CustomerID>ALFKI</CustomerID>  
      <CompanyName>Alfreds Futterkiste</CompanyName>  
    </Customers>  
  </diffgr:before>  
  <diffgr:errors>  
    <Customers diffgr:id="Customers2" diffgr:Error="An optimistic concurrency violation has occurred for this row."/>  
  </diffgr:errors>  
</diffgr:diffgram>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie języka XML w elemencie DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Ładowanie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Zapisywanie zawartości elementu DataSet jako danych XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
