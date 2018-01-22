---
title: "Narzędzie generowania serializatora XML (Sgen.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc1d1f1c-fb26-4be9-885a-3fe84c81cec6
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 10914281632a6651b3872485b795d9a636dc6bd0
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="xml-serializer-generator-tool-sgenexe"></a>Narzędzie generowania serializatora XML (Sgen.exe)
Generator serializatora XML tworzy zestawu serializacji XML dla typów w określonym zestawie w celu zwiększenia wydajności uruchamiania <xref:System.Xml.Serialization.XmlSerializer> po serializuje lub deserializuje obiektów określonego typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
sgen [options]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/a**[**ssembly**] **: *** filename*|Generuje kod serializacji dla wszystkich typów zawartych w zestawie lub plik wykonywalny określony przez *filename*. Można uwzględnić tylko jeden PLik. Jeśli ten argument jest powtarzany, nazwisko PLik jest używany.|  
|**/c [ompiler]:** *opcje*|Określa opcje do przekazania do kompilatora C#. Wszystkie opcje csc.exe są obsługiwane, gdy przekazywane do kompilator. To może posłużyć do określenia zestawu powinny być podpisane i określ PLik klucza.|  
|**/d**[**ebug**]|Generuje obrazu, który może być używany z debugera.|  
|**/ f [orce]**|Wymusza zastępowanie istniejącego zestawu o tej samej nazwie. Wartość domyślna to **false**.|  
|**/ help lub /?**|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/k**[**Zachowaj**]|Pomija usuwanie wygenerowanych PLików źródłowych i innych PLików tymczasowych po zostały skompilowane do zestawu serializacji. To może posłużyć do określenia, czy to narzędzie jest generowania kodu serializacji dla danego typu.|  
|**/n**[**ologo**]|Pomija wyświetlanie transparentu firmy Microsoft.|  
|**/o**[**ut**] **: *** ścieżki*|Określa katalog, w którym chcesz zapisać wygenerowanego zestawu. **Uwaga:** nazwę zestawu wygenerowanego składa się z nazwy zestawu wejściowego plus "xmlSerializers.dll".|  
|**/p**[**roxytypes**]|Generuje kod serializacji tylko dla typów serwera proxy usług sieci Web XML.|  
|**/r**[**większ**] **: *** assemblyfiles*|Określa zestawy, które są określone przez typy wymagające serializacji XML. Akceptuje wiele plików zestawu rozdzielonych przecinkami.|  
|**/s**[**ilent**]|Pomija wyświetlanie komunikatów o sukcesie.|  
|**/t**[**ypu**] **: *** typu*|Generuje kod serializacji tylko dla określonego typu.|  
|**/v**[**erbose**]|Wyświetla pełne dane wyjściowe do debugowania. Wyświetla listę typów z zestawu docelowego, który nie może być serializowany z <xref:System.Xml.Serialization.XmlSerializer>.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy Generator serializatora XML nie jest używany, <xref:System.Xml.Serialization.XmlSerializer> generuje kodu serializacji i zestawu serializacji dla każdego typu w każdym uruchomieniu aplikacji. Aby poprawić wydajność uruchamiania serializacji XML, należy użyć narzędzia Sgen.exe do wygenerowania tych zestawów z wyprzedzeniem. Następnie można wdrożyć te zestawy z aplikacją.  
  
 Generator serializatora XML może również zwiększyć wydajność klientów korzystających z serwerów proxy usług sieci Web XML do komunikowania się z serwerami, ponieważ ten proces serializacji nie będą powodować wydajności trafień, gdy typ jest ładowany po raz pierwszy.  
  
 Nie można używać tych wygenerowanych zestawów po stronie serwera usługi sieci Web. Narzędzie to jest tylko dla klientów usługi sieci Web i scenariusze ręczne serializacji.  
  
 Jeśli zestawu zawierającego typ do serializacji nosi MyType.dll, następnie zestawu skojarzonego serializacji będzie miał nazwę MyType.XmlSerializers.dll.  
  
## <a name="examples"></a>Przykłady  
 Następujące polecenie tworzy zestaw o nazwie Data.XmlSerializers.dll dla wszystkich typów, które są zawarte w zestawie o nazwie Data.dll serializacji.  
  
```  
sgen Data.dll   
```  
  
 Zestaw Data.XmlSerializers.dll można odwoływać się z kodu, który musi serializacji i deserializacji typów w Data.dll.  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia](../../../docs/framework/tools/index.md)  
 [Omówienie usług XML sieci Web](http://msdn.microsoft.com/library/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d)  
 [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
