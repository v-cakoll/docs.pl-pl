---
title: Narzędzie generatora serializatora XML (Sgen.exe)
ms.date: 03/30/2017
ms.assetid: cc1d1f1c-fb26-4be9-885a-3fe84c81cec6
ms.openlocfilehash: 0eb937d003da02322c097d0eda0c3f8769f97dc8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640156"
---
# <a name="xml-serializer-generator-tool-sgenexe"></a>Narzędzie generatora serializatora XML (Sgen.exe)
Generator serializatora XML tworzy zestawu serializacji XML dla typów w określonym zestawie w celu zwiększenia wydajności uruchamiania <xref:System.Xml.Serialization.XmlSerializer> po serializuje lub deserializuje obiektów określonego typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
sgen [options]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/a\[zestawu\]:**_nazwy pliku_|Generuje kod serializacji dla wszystkich typów zawartych w zestawie lub plik wykonywalny określony przez *filename*. Można uwzględnić tylko jeden PLik. Jeśli ten argument jest powtarzany, nazwisko PLik jest używany.|  
|**/c\[ompiler\]:**_opcje_|Określa opcje do przekazania do kompilatora C#. Wszystkie opcje csc.exe są obsługiwane, gdy przekazywane do kompilator. To może posłużyć do określenia zestawu powinny być podpisane i określ PLik klucza.|  
|**/d\[ebug\]**|Generuje obrazu, który może być używany z debugera.|  
|**/f\[orce\]**|Wymusza zastępowanie istniejącego zestawu o tej samej nazwie. Wartość domyślna to **false**.|  
|**/ help lub /?**|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/k\[Zachowaj\]**|Pomija usuwanie wygenerowanych PLików źródłowych i innych PLików tymczasowych po zostały skompilowane do zestawu serializacji. To może posłużyć do określenia, czy to narzędzie jest generowania kodu serializacji dla danego typu.|  
|**/n\[ologo\]**|Pomija wyświetlanie transparentu startowego firmy Microsoft.|  
|**/o\[ut\]:**_ścieżki_|Określa katalog, w którym chcesz zapisać wygenerowanego zestawu. **Uwaga:**  Nazwa zestawu wygenerowanego składa się z nazwy zestawu wejściowego oraz "xmlSerializers.dll".|  
|**/p\[roxytypes\]**|Generuje kod serializacji tylko dla typów serwera proxy usług sieci Web XML.|  
|**/r\[większ\]:**_assemblyfiles_|Określa zestawy, które są określone przez typy wymagające serializacji XML. Akceptuje kilka plików zestawu oddzielonych przecinkami.|  
|**/s\[ilent\]**|Pomija wyświetlanie komunikatów o sukcesie.|  
|**/t\[yp\]:**_typu_|Generuje kod serializacji tylko dla określonego typu.|  
|**/v\[erbose\]**|Wyświetla pełne dane wyjściowe do debugowania. Wyświetla listę typów z zestawu docelowego, który nie może być serializowany z <xref:System.Xml.Serialization.XmlSerializer>.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli Generator serializatora XML nie jest używana, <xref:System.Xml.Serialization.XmlSerializer> generuje kod serializacji i zestawu serializacji dla każdego typu za każdym razem, gdy aplikacja jest uruchamiana. Aby zwiększyć wydajność uruchamiania serializacji XML, narzędzie Sgen.exe do generowania te zestawy z wyprzedzeniem. Następnie można wdrożyć te zestawy z aplikacją.  
  
 Generator serializatora XML może również zwiększyć wydajność klientów korzystających z serwerów proxy usług sieci Web XML do komunikowania się z serwerami, ponieważ ten proces serializacji nie będą powodować wydajności trafień, gdy typ jest ładowany po raz pierwszy.  
  
 Nie można używać tych wygenerowanych zestawów po stronie serwera usługi sieci Web. Narzędzie to jest tylko dla klientów usługi sieci Web i scenariusze ręczne serializacji.  
  
 Jeśli zestawu zawierającego typ do serializacji nosi MyType.dll, następnie zestawu skojarzonego serializacji będzie miał nazwę MyType.XmlSerializers.dll.  
  
## <a name="examples"></a>Przykłady  
 Następujące polecenie tworzy zestaw o nazwie Data.XmlSerializers.dll dla wszystkich typów, które są zawarte w zestawie o nazwie Data.dll serializacji.  
  
```  
sgen Data.dll   
```  
  
 Zestaw Data.XmlSerializers.dll można odwoływać się z kodu, który musi serializacji i deserializacji typów w Data.dll.  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzia](../../../docs/framework/tools/index.md)
- [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
