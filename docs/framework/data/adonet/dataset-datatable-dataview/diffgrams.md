---
title: Elementy DiffGram
ms.date: 03/30/2017
ms.assetid: 037f3991-7bbc-424b-b52e-8b03585d3e34
ms.openlocfilehash: 2c521ef33c98234dac5f4b819a800cd524218462
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151159"
---
# <a name="diffgrams"></a>Elementy DiffGram
DiffGram to format XML identyfikująca bieżące i oryginalne wersje elementów danych. Używa <xref:System.Data.DataSet> formatu DiffGram do ładowania i utrwalania jego zawartości oraz do serializacji jego zawartości do transportu przez połączenie sieciowe. Gdy <xref:System.Data.DataSet> a jest zapisywany jako DiffGram, wypełnia DiffGram ze wszystkimi niezbędnymi informacjami, aby dokładnie odtworzyć zawartość, choć nie schemat, <xref:System.Data.DataSet>wartości kolumn, w tym wartości kolumn zarówno z wersji **wiersza oryginalnego** i **bieżącego,** informacji o błędzie wiersza i kolejności wierszy.  
  
 Podczas wysyłania <xref:System.Data.DataSet> i pobierania z usługi sieci Web XML format DiffGram jest niejawnie używany. <xref:System.Data.DataSet> Ponadto podczas ładowania zawartości z XML przy użyciu metody **ReadXml** lub podczas <xref:System.Data.DataSet> zapisywania zawartości w formacie XML przy użyciu **metody WriteXml** można określić, że zawartość będzie odczytywana lub zapisywana jako DiffGram. Aby uzyskać więcej informacji, zobacz [Ładowanie zestawu danych z pliku XML](loading-a-dataset-from-xml.md) i [zapisywanie zawartości zestawu danych jako danych XML](writing-dataset-contents-as-xml-data.md).  
  
 Format DiffGram jest używany głównie przez program .NET Framework jako format <xref:System.Data.DataSet>serializacji dla zawartości programu , można również używać diffgramów do modyfikowania danych w tabelach w bazie danych programu Microsoft SQL Server.  
  
 Diffgram jest generowany przez zapisanie zawartości wszystkich tabel do ** \<diffgram>** element.  
  
### <a name="to-generate-a-diffgram"></a>Aby wygenerować diffgram  
  
1. Generowanie listy tabel głównych (czyli tabel bez żadnych nadrzędnych).  
  
2. Dla każdej tabeli i jej elementów podrzędnych na liście zapisz bieżącą wersję wszystkich wierszy w pierwszej sekcji Diffgram.  
  
3. Dla każdej tabeli w <xref:System.Data.DataSet>, wypisuj oryginalną wersję wszystkich wierszy, jeśli istnieje, w sekcji ** \<przed>** Diffgram.  
  
4. W przypadku wierszy, które mają błędy, zapisz zawartość błędu w ** \<błędach>** sekcji Diffgram.  
  
 Diffgram jest przetwarzany w kolejności od początku pliku XML do końca.  
  
### <a name="to-process-a-diffgram"></a>Aby przetworzyć diffgram  
  
1. Przetwórz pierwszą sekcję Diffgram, która zawiera bieżącą wersję wierszy.  
  
2. Przetwórz drugą lub ** \<przed>** sekcję zawierającą oryginalną wersję wiersza zmodyfikowanych i usuniętych wierszy.  
  
    > [!NOTE]
    > Jeśli wiersz jest oznaczony jako usunięty, operacja usuwania może również usunąć `Cascade` elementy podrzędne <xref:System.Data.DataSet>wiersza, w zależności od właściwości bieżącego .  
  
3. Przetwórz ** \<błędy>** sekcji. Ustaw informacje o błędzie dla określonego wiersza i kolumny dla każdego elementu w tej sekcji.  
  
> [!NOTE]
> Jeśli ustawisz <xref:System.Data.XmlWriteMode> diffgram, zawartość obiektu <xref:System.Data.DataSet> docelowego <xref:System.Data.DataSet> i oryginału może się różnić.  
  
## <a name="diffgram-format"></a>DiffGram Format  
 Format DiffGram jest podzielony na trzy sekcje: bieżące dane, oryginalne (lub "przed") i sekcję błędów, jak pokazano w poniższym przykładzie.  
  
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
  
 Format DiffGram składa się z następujących bloków danych:  
  
 **\<**  ***Datainstance***  **>**  
 Nazwa tego elementu, ***DataInstance***, jest używana do celów wyjaśnienia w tej dokumentacji. A ***DataInstance*** element <xref:System.Data.DataSet> reprezentuje lub <xref:System.Data.DataTable>wiersz . Zamiast *DataInstance*, element będzie zawierać nazwę <xref:System.Data.DataSet> <xref:System.Data.DataTable>lub . Ten blok formatu DiffGram zawiera bieżące dane, niezależnie od tego, czy zostały zmodyfikowane, czy nie. Element lub wiersz, który został zmodyfikowany jest identyfikowany za pomocą **diffgr:hasChanges** adnotacji.  
  
 **\<diffgr:przed>**  
 Ten blok formatu DiffGram zawiera oryginalną wersję wiersza. Elementy w tym bloku są dopasowywać do elementów w bloku ***DataInstance*** przy użyciu **diffgr:id** adnotacji.  
  
 **\<diffgr:błędy>**  
 Ten blok formatu DiffGram zawiera informacje o błędzie dla określonego wiersza w bloku ***DataInstance.*** Elementy w tym bloku są dopasowywać do elementów w bloku ***DataInstance*** przy użyciu **diffgr:id** adnotacji.  
  
## <a name="diffgram-annotations"></a>Adnotacje diffgram  
 DiffGramy używają kilku adnotacji do wiązki elementów z różnych bloków DiffGram, które reprezentują różne wersje wierszy lub informacje o błędzie w <xref:System.Data.DataSet>pliku .  
  
 W poniższej tabeli opisano adnotacje DiffGram zdefiniowane w urny obszaru nazw **DiffGram:schemas-microsoft-com:xml-diffgram-v1**.  
  
|Adnotacja|Opis|  
|----------------|-----------------|  
|**Identyfikator**|Służy do parowania elementów w ** \<diffgr:before>** i **\<** **>** ** \<diffgr:errors>** bloków do elementów w bloku ***DataInstance.*** Wartości z adnotacją **diffgr:id** są w formie *[TableName][RowIdentifier]*. Na przykład: `<Customers diffgr:id="Customers1">`.|  
|**Parentid**|Identyfikuje, który element **\<** z bloku ***DataInstance*** **>** jest elementem nadrzędnym bieżącego elementu. Wartości z **adnotacją diffgr:parentId** są w formie *[TableName][RowIdentifier]*. Na przykład: `<Orders diffgr:parentId="Customers1">`.|  
|**Haschanges**|Identyfikuje wiersz w **\<** bloku ***DataInstance*** **>** jako zmodyfikowany. Adnotacje **hasChanges** mogą mieć jedną z następujących dwóch wartości:<br /><br /> **Wstawiony**<br /> Identyfikuje **wiersz Dodany.**<br /><br /> **Zmodyfikowano**<br /> Identyfikuje **zmodyfikowany** wiersz, który zawiera **oryginalną** wersję wiersza ** \<w diffgr:before>** bloku. Należy zauważyć, że **usunięte** wiersze będą miały **oryginalną** wersję wiersza w ** \<diffgr:before>** **\<** bloku, ale nie będzie żadnego elementu z adnotacjami w bloku ***DataInstance.*** **>**|  
|**Haserrors**|**\<** Identyfikuje wiersz w bloku ***DataInstance*** **>** za pomocą **rowerror**. Element błędu jest umieszczany w ** \<diffgr:errors>** bloku.|  
|**Błąd**|Zawiera tekst **RowError** dla określonego elementu w ** \<diffgr:errors>** bloku.|  
  
 Zawiera <xref:System.Data.DataSet> dodatkowe adnotacje podczas odczytywania lub zapisywania jego zawartość jako DiffGram. W poniższej tabeli opisano te dodatkowe adnotacje, które są zdefiniowane w urny obszaru **nazw:schemas-microsoft-com:xml-msdata**.  
  
|Adnotacja|Opis|  
|----------------|-----------------|  
|**WierszOrder**|Zachowuje kolejność wierszy oryginalnych danych i identyfikuje indeks wiersza <xref:System.Data.DataTable>w określonym pliku .|  
|**Ukryty**|Identyfikuje kolumnę jako mającą właściwość **ColumnMapping** ustawioną na **MappingType.Hidden**. Atrybut jest napisany w formacie **msdata:hidden** *[ColumnName]*="*value*". Na przykład: `<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">`.<br /><br /> Należy zauważyć, że ukryte kolumny są zapisywane jako atrybut DiffGram tylko wtedy, gdy zawierają dane. W przeciwnym razie są one ignorowane.|  
  
## <a name="sample-diffgram"></a>Przykładowy DiffGram  
 Poniżej przedstawiono przykład formatu DiffGram. W tym przykładzie przedstawiono wynik aktualizacji wiersza w tabeli przed zatwierdzeniem zmian. Wiersz z identyfikatorem klienta "ALFKI" został zmodyfikowany, ale nie został zaktualizowany. W rezultacie istnieje **bieżący** wiersz z **diffgr:id** "Customers1" **\<** w bloku ***DataInstance*** **>** i **Original** wiersz z **diffgr:id** "Customers1" w ** \<diffgr:before>** bloku. Wiersz z CustomerID "ANATR" zawiera **RowError**, więc jest `diffgr:hasErrors="true"` adnotacjami i istnieje powiązany element w ** \<diffgr:errors>** bloku.  
  
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

- [Używanie języka XML w elemencie DataSet](using-xml-in-a-dataset.md)
- [Ładowanie elementu DataSet z pliku XML](loading-a-dataset-from-xml.md)
- [Zapisywanie zawartości elementu DataSet jako danych XML](writing-dataset-contents-as-xml-data.md)
- [Elementy DataSet, DataTable i DataView](index.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
