---
title: Narzędzie generatora serializatora XML (Sgen.exe)
description: Generator serializatora XML tworzy zestaw serializacji XML dla typów w zestawie, który zwiększa wydajność uruchamiania XmlSerializer.
ms.date: 03/30/2017
ms.assetid: cc1d1f1c-fb26-4be9-885a-3fe84c81cec6
ms.openlocfilehash: b6d9406ca6a69f7bdff3129b55c89dd5d1589d3f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288943"
---
# <a name="xml-serializer-generator-tool-sgenexe"></a>Narzędzie generatora serializatora XML (Sgen.exe)

Generator serializatora XML tworzy zestaw serializacji XML dla typów w określonym zestawie. Zestaw serializacji poprawia wydajność uruchamiania <xref:System.Xml.Serialization.XmlSerializer> podczas serializacji lub deserializacji obiektów określonych typów.
  
## <a name="syntax"></a>Składnia

Uruchom narzędzie z wiersza polecenia.
  
```console  
sgen [options]  
```
  
> [!TIP]
> Aby narzędzia .NET Framework działały prawidłowo, należy odpowiednio ustawić `Path` `Include` `Lib` zmienne środowiskowe, i. Ustaw te zmienne środowiskowe, uruchamiając SDKVars. bat, który znajduje się w \<SDK> katalogu \v2.0\bin. SDKVars.bat muszą zostać wykonane w każdym powłoki poleceń.
  
## <a name="parameters"></a>Parametry  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/a \[ ssembly \] :**_filename_|Generuje kod serializacji dla wszystkich typów zawartych w zestawie lub pliku wykonywalnym określonym przez *filename*. Można uwzględnić tylko jeden PLik. Jeśli ten argument jest powtarzany, nazwisko PLik jest używany.|  
|**/c \[ ompiler \] :**_Opcje_|Określa opcje do przekazania do kompilatora C#. Wszystkie opcje csc.exe są obsługiwane, gdy przekazywane do kompilator. To może posłużyć do określenia zestawu powinny być podpisane i określ PLik klucza.|  
|**/d \[ ebug\]**|Generuje obrazu, który może być używany z debugera.|  
|**/f \[ Orce\]**|Wymusza zastępowanie istniejącego zestawu o tej samej nazwie. Wartość domyślna to **false**.|  
|**/help lub/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/k \[ achowaj\]**|Pomija usuwanie wygenerowanych PLików źródłowych i innych PLików tymczasowych po zostały skompilowane do zestawu serializacji. To może posłużyć do określenia, czy to narzędzie jest generowania kodu serializacji dla danego typu.|  
|**/n \[ ologo\]**|Pomija wyświetlanie transparentu startowego firmy Microsoft.|  
|**/o \[ UT \] :**_ścieżka_|Określa katalog, w którym chcesz zapisać wygenerowanego zestawu. **Uwaga:**  Nazwa wygenerowanego zestawu składa się z nazwy zestawu wejściowego i "XmlSerializers. dll".|  
|**/p \[ roxytypes\]**|Generuje kod serializacji tylko dla typów serwera proxy usług sieci Web XML.|  
|**/r \[ eference \] :**_assemblyfiles_|Określa zestawy, które są określone przez typy wymagające serializacji XML. Akceptuje wiele plików zestawów rozdzielonych przecinkami.|  
|**/s \[ ilent\]**|Pomija wyświetlanie komunikatów o sukcesie.|  
|**/t \[ Typ \] :**_Typ_|Generuje kod serializacji tylko dla określonego typu.|  
|**/v \[ erbose\]**|Wyświetla pełne dane wyjściowe dla debugowania. Wyświetla listę typów z zestawu docelowego, który nie może być serializowany z <xref:System.Xml.Serialization.XmlSerializer>.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy generator serializatorów XML nie jest używany, <xref:System.Xml.Serialization.XmlSerializer> generuje kod serializacji i zestaw serializacji dla każdego typu za każdym razem, gdy aplikacja jest uruchamiana. Aby zwiększyć wydajność uruchamiania serializacji XML, należy użyć narzędzia Sgen. exe w celu wygenerowania tych zestawów z góry. Zestawy te można następnie wdrażać za pomocą aplikacji.  
  
 Generator serializatora XML może również zwiększyć wydajność klientów korzystających z serwerów proxy usług sieci Web XML do komunikowania się z serwerami, ponieważ ten proces serializacji nie będą powodować wydajności trafień, gdy typ jest ładowany po raz pierwszy.  
  
 Nie można używać tych wygenerowanych zestawów po stronie serwera usługi sieci Web. Narzędzie to jest tylko dla klientów usługi sieci Web i scenariusze ręczne serializacji.  
  
 Jeśli zestawu zawierającego typ do serializacji nosi MyType.dll, następnie zestawu skojarzonego serializacji będzie miał nazwę MyType.XmlSerializers.dll.  
  
## <a name="examples"></a>Przykłady  
 Następujące polecenie tworzy zestaw o nazwie Data.XmlSerializers.dll dla wszystkich typów, które są zawarte w zestawie o nazwie Data.dll serializacji.  
  
```console  
sgen Data.dll
```  
  
 Zestaw Data.XmlSerializers.dll można odwoływać się z kodu, który musi serializacji i deserializacji typów w Data.dll.  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzia](../../framework/tools/index.md)
- [Wiersze poleceń](../../framework/tools/developer-command-prompt-for-vs.md)
