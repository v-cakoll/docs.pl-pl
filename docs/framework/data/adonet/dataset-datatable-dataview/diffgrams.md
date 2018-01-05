---
title: DataSets
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 037f3991-7bbc-424b-b52e-8b03585d3e34
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6166cae86d2956ae3eec28b98fe0af864f6b708b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="diffgrams"></a>DataSets
Elementu DiffGram jest w formacie XML, który identyfikuje bieżące i oryginalne wersje elementów danych. <xref:System.Data.DataSet> Używa formatu elementu DiffGram do ładowania i utrwalić jego zawartość, a do serializacji jego zawartość dla transportu przez połączenie sieciowe. Gdy <xref:System.Data.DataSet> są zapisywane jako elementu DiffGram wypełnia elementu DiffGram niezbędne informacje, aby dokładnie odtworzyć zawartość, jednak nie schematu z <xref:System.Data.DataSet>, łącznie z obu wartości w kolumnie **oryginalne** i **bieżącego** wersje wiersza, informacje o błędzie wiersza i kolejności wierszy.  
  
 Podczas wysyłania i pobierania <xref:System.Data.DataSet> z usługi XML sieci Web niejawnie używany jest format elementu DiffGram. Ponadto podczas ładowania zawartości <xref:System.Data.DataSet> z XML za pomocą **ReadXml** metody, lub podczas zapisywania zawartości <xref:System.Data.DataSet> za pomocą XML **WriteXml** metody, można określić czy zawartość odczytu lub zapisu jako elementu DiffGram. Aby uzyskać więcej informacji, zobacz [podczas ładowania zestawu danych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) i [zapisywanie zawartości zestawu danych jako dane XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 Format elementu DiffGram jest głównie używane w programie .NET Framework jako formatu serializacji zawartości <xref:System.Data.DataSet>, umożliwia także DataSets zmodyfikować dane w tabelach w bazie danych programu Microsoft SQL Server.  
  
 Elementu Diffgram jest generowany przez zapisywanie zawartości wszystkich tabel do  **\<elementu diffgram >** elementu.  
  
### <a name="to-generate-a-diffgram"></a>Aby wygenerować obiektu Diffgram  
  
1.  Generowanie listy tabel głównego (to znaczy tabele bez żadnych nadrzędnego).  
  
2.  Dla każdej tabeli i jego elementy podrzędne na liście zapisać bieżącą wersję wszystkich wierszy w pierwszej sekcji elementu Diffgram.  
  
3.  Dla każdej tabeli w <xref:System.Data.DataSet>, Zapisz oryginalnej wersji wszystkie wiersze w  **\<przed >** części elementu Diffgram.  
  
4.  Dla wierszy zawierających błędy zapisu zawartości w błąd  **\<błędy >** części elementu Diffgram.  
  
 Elementu Diffgram są przetwarzane w kolejności od początku pliku XML na końcu.  
  
### <a name="to-process-a-diffgram"></a>Do elementu Diffgram procesu  
  
1.  Proces w pierwszej sekcji elementu Diffgram, zawierający bieżącą wersję wierszy.  
  
2.  Przetwarzanie drugi lub  **\<przed >** sekcję zawierającą z oryginalną wersją wiersza zmodyfikowane i usuniętych wierszy.  
  
    > [!NOTE]
    >  Jeśli wiersz jest oznaczony jako usunięte, operacja usuwania można usunąć wiersza elementy podrzędne również, w zależności od `Cascade` właściwości bieżącego <xref:System.Data.DataSet>.  
  
3.  Proces  **\<błędy >** sekcji. Ustaw informacje o błędzie dla określonych wiersza i kolumny dla każdego elementu w tej sekcji.  
  
> [!NOTE]
>  Jeśli ustawisz <xref:System.Data.XmlWriteMode> do elementu Diffgram, zawartość elementu docelowego <xref:System.Data.DataSet> i oryginalny <xref:System.Data.DataSet> mogą się różnić.  
  
## <a name="diffgram-format"></a>Format elementu DiffGram  
 Format elementu DiffGram jest podzielone na trzy części: bieżące dane, oryginalne (lub "przed") danych i sekcji błędy, jak pokazano w poniższym przykładzie.  
  
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
  
 Format elementu DiffGram składa się z następujących bloków danych:  
  
 **\<**  ***DataInstance***  **>**  
 Nazwa tego elementu ***DataInstance***, jest używana do celów wyjaśnienie w niniejszej dokumentacji. A ***DataInstance*** reprezentuje element <xref:System.Data.DataSet> lub wiersz <xref:System.Data.DataTable>. Zamiast *DataInstance*, zawiera nazwę elementu <xref:System.Data.DataSet> lub <xref:System.Data.DataTable>. Ten blok format elementu DiffGram zawiera bieżące dane, czy został on zmodyfikowany lub nie. Element lub wiersza, który został zmodyfikowany, jest oznaczone symbolem **diffgr:hasChanges** adnotacji.  
  
 **\<diffgr: przed >**  
 Ten blok format elementu DiffGram zawiera oryginalnej wersji wiersza. Elementy w tym bloku są dopasowywane do elementów w ***DataInstance*** zablokowane, używając **diffgr:id** adnotacji.  
  
 **\<diffgr:errors >**  
 Ten blok format elementu DiffGram zawiera informacje o błędzie dla danego wiersza w ***DataInstance*** bloku. Elementy w tym bloku są dopasowywane do elementów w ***DataInstance*** zablokowane, używając **diffgr:id** adnotacji.  
  
## <a name="diffgram-annotations"></a>Adnotacje elementu DiffGram  
 DataSets użyć kilku adnotacje do powiązania elementów z innego elementu DiffGram bloki wersje innego wiersza lub informacje o błędzie w <xref:System.Data.DataSet>.  
  
 W poniższej tabeli opisano adnotacje elementu DiffGram, które są zdefiniowane w przestrzeni nazw elementu DiffGram **urn: schemas-microsoft-com: XML-elementu diffgram-v1**.  
  
|Adnotacja|Opis|  
|----------------|-----------------|  
|**id**|Używany do elementów w parę  **\<diffgr: przed >** i  **\<diffgr:errors >** bloków do elementów w  **\<**  ***DataInstance***  **>**  bloku. Wartości z **diffgr:id** adnotacji mają postać *[Nazwa_tabeli] [RowIdentifier]*. Na przykład: `<Customers diffgr:id="Customers1">`.|  
|**Parametr parentId**|Identyfikuje element, który z  **\<**  ***DataInstance***  **>**  bloku jest elementem nadrzędnym bieżącego elementu. Wartości z **diffgr:parentId** adnotacji mają postać *[Nazwa_tabeli] [RowIdentifier]*. Na przykład: `<Orders diffgr:parentId="Customers1">`.|  
|**hasChanges**|Identyfikuje wiersz w  **\<**  ***DataInstance***  **>**  zablokować zmienione. **HasChanges** adnotacji może mieć jedną z następujących dwóch wartości:<br /><br /> **dodaje**<br /> Identyfikuje **Added** wiersza.<br /><br /> **zmodyfikowane**<br /> Identyfikuje **zmodyfikowane** wiersza, który zawiera **oryginalnego** wersja wiersza w  **\<diffgr: przed >** bloku. Należy pamiętać, że **usunięte** wierszy będą miały **oryginalnego** wersja wiersza w  **\<diffgr: przed >** bloku, ale będą się żaden element adnotacjami w  **\<**  ***DataInstance***  **>**  bloku.|  
|**hasErrors**|Identyfikuje wiersz w  **\<**  ***DataInstance***  **>**  zablokować z **RowError**. Błędny element znajduje się w  **\<diffgr:errors >** bloku.|  
|**Błąd**|Tekst zawiera **RowError** dla określonego elementu w  **\<diffgr:errors >** bloku.|  
  
 <xref:System.Data.DataSet> Obejmuje dodatkowych adnotacji podczas odczytywania lub zapisywania jego zawartość jako elementu DiffGram. W poniższej tabeli opisano te dodatkowe adnotacje, które są zdefiniowane w przestrzeni nazw **urn: schemas-microsoft-com: XML-msdata**.  
  
|Adnotacja|Opis|  
|----------------|-----------------|  
|**RowOrder**|Zachowuje kolejności wierszy oryginalnych danych i identyfikuje indeks wiersza, w szczególności <xref:System.Data.DataTable>.|  
|**Ukryte**|Identyfikuje kolumny jako mający **ColumnMapping** ustawioną właściwość **MappingType.Hidden**. Ten atrybut jest zapisywany w formacie **msdata: ukryte** *[nazwa_kolumny]*= "*wartość*". Na przykład: `<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">`.<br /><br /> Należy pamiętać, że ukrytych kolumn tylko są zapisywane jako atrybut elementu DiffGram, jeśli zawierają one dane. W przeciwnym razie są ignorowane.|  
  
## <a name="sample-diffgram"></a>Przykład elementu DiffGram  
 Poniżej przedstawiono przykład formatu elementu DiffGram. Ten przykład przedstawia wynik aktualizacja wiersza w tabeli, aby zmiany zostały przekazane. Wiersz z CustomerID "ALFKI" został zmodyfikowany, ale nie zostały zaktualizowane. W związku z tym istnieje **bieżącego** wiersz z **diffgr:id** z "Przekształcana w nazwę Klienci1" w  **\<**  ***DataInstance***  **>**  bloku, a **oryginalnego** wiersz z **diffgr:id** z "Przekształcana w nazwę Klienci1" w  **\<diffgr: przed >**bloku. Zawiera wiersz z CustomerID "ANATR" **RowError**, więc jest adnotowany przy `diffgr:hasErrors="true"` i jest elementem pokrewne  **\<diffgr:errors >** bloku.  
  
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
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
