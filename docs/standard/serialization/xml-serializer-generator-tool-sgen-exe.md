---
title: Narzędzie generatora serializatora XML (Sgen.exe)
ms.date: 03/30/2017
ms.assetid: cc1d1f1c-fb26-4be9-885a-3fe84c81cec6
ms.openlocfilehash: bc1a0abaeef9a9244aa83941e590063c7ef167d1
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588365"
---
# <a name="xml-serializer-generator-tool-sgenexe"></a>Narzędzie generatora serializatora XML (Sgen.exe)

Generator serializatora XML tworzy zestaw serializacji XML dla typów w określonym zestawie. Zestaw serializacji zwiększa wydajność uruchamiania <xref:System.Xml.Serialization.XmlSerializer> podczas serializacji lub deserializacji obiektów określonych typów.
  
## <a name="syntax"></a>Składnia

Uruchom narzędzie z wiersza polecenia.
  
```console  
sgen [options]  
```
  
> [!TIP]
> Aby narzędzia platformy .NET Framework działały `Path`poprawnie, należy poprawnie ustawić `Include`zmienne , i `Lib` środowiskowe. Ustaw te zmienne środowiskowe, uruchamiając plik SDKVars.bat, który znajduje się w katalogu \<SDK>\v2.0\Bin. SDKVars.bat muszą zostać wykonane w każdym powłoki poleceń.
  
## <a name="parameters"></a>Parametry  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/a\[ssembly\]:** nazwa_pliku_|Generuje kod serializacji dla wszystkich typów zawartych w zestawie lub pliku wykonywalnym określonym przez *nazwę pliku*. Można uwzględnić tylko jeden PLik. Jeśli ten argument jest powtarzany, nazwisko PLik jest używany.|  
|**/c\[ompiler\]:**_opcje_|Określa opcje do przekazania do kompilatora C#. Wszystkie opcje csc.exe są obsługiwane, gdy przekazywane do kompilator. To może posłużyć do określenia zestawu powinny być podpisane i określ PLik klucza.|  
|**/d\[ebug\]**|Generuje obrazu, który może być używany z debugera.|  
|**/f\[orce\]**|Wymusza zastępowanie istniejącego zestawu o tej samej nazwie. Wartość domyślna to **false**.|  
|**/help lub /?**|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/k\[eep\]**|Pomija usuwanie wygenerowanych PLików źródłowych i innych PLików tymczasowych po zostały skompilowane do zestawu serializacji. To może posłużyć do określenia, czy to narzędzie jest generowania kodu serializacji dla danego typu.|  
|**/n\[ologo\]**|Pomija wyświetlanie banera startowego firmy Microsoft.|  
|**/o\[\]ut :**_ścieżka_|Określa katalog, w którym chcesz zapisać wygenerowanego zestawu. **Uwaga:**  Nazwa wygenerowanego zestawu składa się z nazwy zestawu wejściowego oraz "xmlSerializers.dll".|  
|**/p\[roxytypes\]**|Generuje kod serializacji tylko dla typów serwera proxy usług sieci Web XML.|  
|**/r\[eference\]:** pliki_montażowe_|Określa zestawy, które są określone przez typy wymagające serializacji XML. Akceptuje wiele plików zestawu oddzielonych przecinkami.|  
|**/s\[ilent\]**|Pomija wyświetlanie komunikatów o sukcesie.|  
|**/t\[\]ype :**_typ_|Generuje kod serializacji tylko dla określonego typu.|  
|**/v\[erbose\]**|Wyświetla pełne dane wyjściowe do debugowania. Wyświetla listę typów z zestawu docelowego, który nie może być serializowany z <xref:System.Xml.Serialization.XmlSerializer>.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy generator serializatora XML nie <xref:System.Xml.Serialization.XmlSerializer> jest używany, generuje kod serializacji i zestaw serializacji dla każdego typu za każdym razem, gdy aplikacja jest uruchamiana. Aby zwiększyć wydajność uruchamiania serializacji XML, użyj narzędzia Sgen.exe, aby wygenerować te zestawy z wyprzedzeniem. Zestawy te można następnie wdrożyć za pomocą aplikacji.  
  
 Generator serializatora XML może również zwiększyć wydajność klientów korzystających z serwerów proxy usług sieci Web XML do komunikowania się z serwerami, ponieważ ten proces serializacji nie będą powodować wydajności trafień, gdy typ jest ładowany po raz pierwszy.  
  
 Nie można używać tych wygenerowanych zestawów po stronie serwera usługi sieci Web. Narzędzie to jest tylko dla klientów usługi sieci Web i scenariusze ręczne serializacji.  
  
 Jeśli zestawu zawierającego typ do serializacji nosi MyType.dll, następnie zestawu skojarzonego serializacji będzie miał nazwę MyType.XmlSerializers.dll.  
  
## <a name="examples"></a>Przykłady  
 Następujące polecenie tworzy zestaw o nazwie Data.XmlSerializers.dll dla wszystkich typów, które są zawarte w zestawie o nazwie Data.dll serializacji.  
  
```console  
sgen Data.dll
```  
  
 Zestaw Data.XmlSerializers.dll można odwoływać się z kodu, który musi serializacji i deserializacji typów w Data.dll.  
  
## <a name="see-also"></a>Zobacz też

- [narzędzia](../../../docs/framework/tools/index.md)
- [Wiersze poleceń](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
