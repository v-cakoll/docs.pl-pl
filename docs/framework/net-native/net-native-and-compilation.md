---
title: Architektura .NET Native i kompilacja
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e38ae4f3-3e3d-42c3-a4b8-db1aa9d84f85
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d86d8a740aa0597a21c6665ee722f4a601dec9bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="net-native-and-compilation"></a>Architektura .NET Native i kompilacja
Aplikacje Windows 8.1 i aplikacje dla komputerów z systemem Windows przeznaczonych dla platformy.NET Framework są zapisywane w określonym języku programowania i skompilowany w języku pośrednim (IL). W czasie wykonywania kompilatora just in time (JIT) jest odpowiedzialny za kompilowanie IL do kodu natywnego dla komputera lokalnego, po prostu, przed wykonaniem metody po raz pierwszy. Z kolei łańcucha narzędzi dla platformy .NET Native konwertuje kodu źródłowego do kodu macierzystego w czasie kompilacji. W tym temacie porównuje platformy .NET Native z innymi technologiami kompilacji dostępne dla aplikacji .NET Framework, a także omówienie praktyczne jak platforma .NET Native tworzy kodu natywnego, które mogą ułatwić zrozumienie, dlaczego wyjątków, które występują w kodzie skompilowanym z .NET Macierzysty nie występują w kodzie kompilacji JIT.  
  
## <a name="net-native-generating-native-binaries"></a>Architektura .NET native: Generowanie natywne pliki binarne  
 Aplikacja, że obiektów docelowych programu .NET Framework i który nie jest skompilowana przy użyciu platformy .NET Native łańcucha narzędzi składa się z zestawu aplikacji, w którym znajdują się następujące:  
  
-   [Metadane](../../../docs/standard/metadata-and-self-describing-components.md) , który opisuje zestaw, zależnościami, zawiera typy i ich elementy członkowskie. Metadane są używane dla dostępu późnym wiązaniem i odbicie, a w niektórych przypadkach przez narzędzia kompilatora i kompilacji.  
  
-   W kodzie. Ten krok składa się z opcodes języku pośrednim (IL). W czasie wykonywania przy użyciu kompilatora just in time (JIT) tłumaczy go do kodu macierzystego dla platformy docelowej.  
  
 Oprócz używanego zestawu aplikacji głównej aplikacji wymaga następujące obecne:  
  
-   Biblioteki klas dodatkowych lub zestawy innych firm, które są wymagane przez aplikację. Te zestawy podobnie obejmować metadane opisujące zestaw, jego typów i ich elementy członkowskie, a także IL, który implementuje wszystkie elementy członkowskie typu.  
  
-   Bibliotece klas programu .NET Framework. Jest to zbiór zestawów, który jest zainstalowany w systemie lokalnym z instalacji programu .NET Framework. Zestawy zawarte w bibliotece klas programu .NET Framework obejmują kompletnego zestawu metadanych i wykonania kodu.  
  
-   Środowisko uruchomieniowe języka wspólnego. To jest kolekcja bibliotek dołączanych dynamicznie, wykonujących usług ładowania zestawu, pamięci zarządzania oraz wyrzucania elementów bezużytecznych, obsługa wyjątków, w czasie kompilacji, usług zdalnych i interop. Jak biblioteka klas środowiska uruchomieniowego jest zainstalowany w systemie lokalnym w ramach instalacji programu .NET Framework.  
  
 Należy pamiętać, że całe środowisko uruchomieniowe języka wspólnego, tak jak metadanych i IL dla wszystkich typów w zestawy specyficzne dla aplikacji, zestawy innych firm i zestawy system musi występować dla aplikacji zostać pomyślnie uruchomiony.  
  
## <a name="net-native-and-just-in-time-compilation"></a>Platforma .NET native i w czasie kompilacji  
 Dane wejściowe dla platformy .NET Native łańcucha narzędzi jest konstruowany przez języka C# lub Visual Basic kompilatora aplikacji ze Sklepu Windows. Innymi słowy łańcucha narzędzi dla platformy .NET Native rozpoczyna się od wykonywania kompilatora języka zakończył kompilacji aplikacji ze Sklepu Windows.  
  
> [!TIP]
>  Ponieważ w danych wejściowych platformy .NET Native IL i zapisane do zarządzanych zestawów metadane, należy nadal wykonać generowania kodu niestandardowego lub innych niestandardowych operacji za pomocą zdarzenia prekompilacyjnego lub mające miejsce po kompilacji lub przez zmodyfikowanie pliku projektu MSBuild.  
>   
>  Kategorie narzędzia, które zmodyfikować IL i tym samym zapobiec łańcucha narzędzi dla platformy .NET analizowanie IL aplikacji nie są obsługiwane. Obfuscators są najbardziej znacząca narzędzia tego typu.  
  
 W trakcie konwersji aplikację z IL do kodu macierzystego, łańcucha narzędzi dla platformy .NET Native wykonuje operacje, takie jak następujące:  
  
-   Dla niektórych ścieżki kodu, zastępuje ona kod korzystający metadanych z kodem natywnym statyczne i odbicia. Na przykład, jeśli typ wartości nie przesłania <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> metoda, testowanie domyślne równości używa odbicia pobrać <xref:System.Reflection.FieldInfo> obiekty reprezentujące pola typu wartości, następnie porównuje dwa wystąpienia wartości pól. W przypadku kompilowania kodu do kodu natywnego, łańcucha narzędzi dla platformy .NET Native zastępuje odbicia kodu i metadanych statycznych porównanie wartości pól.  
  
-   Jeśli to możliwe, podejmie próbę usunięcia wszystkich metadanych.  
  
-   Zawiera zestawy ostatecznej aplikacji tylko kod implementacji faktycznie jest wywoływany przez aplikację. Dotyczy to szczególnie kodu w bibliotekach innych firm oraz w bibliotece klas programu .NET Framework. W związku z tym nie jest już zależy aplikacja bibliotek innych firm lub pełne Framework bibliotece klas programu .NET; Zamiast tego kodu innych firm oraz bibliotek klas .NET Framework jest teraz lokalnego do aplikacji.  
  
-   Zastępuje ona pełnego CLR refactored środowisko uruchomieniowe, które zawiera moduł garbage collector. Refactored środowiska uruchomieniowego znajduje się w bibliotece o nazwie mrt100_app.dll jest lokalny dla aplikacji, która jest tylko kilku kilobajtów kilkuset rozmiar. Jest to możliwe, ponieważ statycznego łączenia eliminuje potrzebę stosowania wiele usługi świadczone przez środowisko uruchomieniowe języka wspólnego.  
  
    > [!NOTE]
    >  Platforma .NET native używa tego samego modułu zbierającego elementy bezużyteczne jako standardowe środowiska CLR. W moduł zbierający elementy bezużyteczne .NET Native odzyskiwanie pamięci w tle jest włączona domyślnie. Aby uzyskać więcej informacji o pamięci, zobacz [podstawowe informacje dotyczące wyrzucania elementów bezużytecznych](../../../docs/standard/garbage-collection/fundamentals.md).  
  
> [!IMPORTANT]
>  Platforma .NET native kompiluje całej aplikacji do natywnej aplikacji. Nie zezwalaj można skompilować jednego zestawu, który zawiera biblioteki klas do kodu natywnego, dzięki czemu można go wywołać niezależnie z kodu zarządzanego.  
  
 Wynikowa aplikację, która jest generowany przez platformę .NET Native łańcucha narzędzi są zapisywane w katalogu o nazwie ilc.out w katalogu debugowanie czy wydanie w katalogu projektu. Składa się z następujących plików:  
  
-   *\<Nazwa aplikacji >*.exe, plik wykonywalny skrótowa, która po prostu transfer kontroli do specjalnego `Main` eksportu w  *\<nazwa_aplikacji >*dll.  
  
-   *\<Nazwa aplikacji >*dll, Windows dynamic link biblioteki, który zawiera kod aplikacji, a także kodu w bibliotece klas programu .NET Framework i biblioteki żadnych innych firm, które zależy od.  Zawiera także kod pomocy technicznej, takich jak kod niezbędne do współpracy z systemem Windows oraz do serializacji obiektów w aplikacji.  
  
-   mrt100_app.dll, refactored środowisko uruchomieniowe, które zapewnia usługi czasu wykonywania, takie jak wyrzucanie elementów bezużytecznych.  
  
 Wszystkie zależności są przechwytywane przez manifest APPX aplikacji.  Oprócz aplikacji exe, dll i mrt100_app.dll, które są połączone bezpośrednio w pakiecie appx obejmuje dwa więcej plików:  
  
-   msvcr140_app.dll, biblioteki czasu wykonywania (CRT) C, używany przez mrt100_app.dll. Polecenie jest zawarte przez odwołanie framework w pakiecie.  
  
-   mrt100.dll. Ta biblioteka zawiera funkcje, które może poprawić wydajność mrt100_app.dll, mimo że jego braku nie uniemożliwia działania mrt100_app.dll. Jest on załadowany w folderze System32 na komputerze lokalnym, jeśli jest obecny.  
  
 Ponieważ łańcucha narzędzi dla platformy .NET Native łączy wykonania kodu w aplikacji tylko wtedy, gdy wiadomo, że aplikacja faktycznie wywołuje ten kod, metadane lub kod implementacji wymagane w następujących scenariuszach może być dołączone do aplikacji:  
  
-   Odbicia.  
  
-   Wywołania z późnym wiązaniem lub dynamicznego.  
  
-   Serializacji i deserializacji.  
  
-   COM interop.  
  
 Jeśli konieczne kod metadanych lub implementacji jest nieobecny w czasie wykonywania, środowisko uruchomieniowe platformy .NET Native zgłasza wyjątek. Można zapobiec te wyjątki i upewnij się, że platforma .NET Native łańcucha narzędzi zawiera wymagane metadane i wykonania kodu, przy użyciu [pliku dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md), plik XML, który wyznacza elementów programu których metadanych lub kod implementacji musi być dostępny w czasie wykonywania i przypisuje zasad wykonywania. Poniżej przedstawiono domyślnego pliku dyrektyw środowiska uruchomieniowego, który zostanie dodany do projektu Sklepu Windows, który ma być kompilowana przez platformę .NET Native łańcucha narzędzi:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
  </Application>  
</Directives>  
```  
  
 Dzięki temu wszystkie typy, a także wszystkich ich elementów członkowskich, do wszystkich zestawów w pakiet aplikacji dla odbicia i dynamiczne wywołanie. Jednak nie umożliwia dynamiczne aktywacji typów w zestawach Biblioteka klas programu .NET Framework lub odbicia. W wielu przypadkach jest to odpowiednie.  
  
## <a name="net-native-and-ngen"></a>Architektura .NET native i NGEN  
 [(Generator obrazu natywnego](../../../docs/framework/tools/ngen-exe-native-image-generator.md) (NGEN) kompiluje zestawów do kodu macierzystego i instaluje je w pamięci podręcznej obrazów natywnych na komputerze lokalnym. Jednak mimo że NGEN, takich jak platforma .NET Native tworzy kodu natywnego, różni się od platformy .NET Native w pewnym sensie znaczących:  
  
-   Jeśli obrazu macierzystego są dostępne dla konkretnej metody, NGEN powraca do JITing kodu. Oznacza to, obrazów macierzystych muszą nadal zawierać metadane i IL w przypadku, gdy NGEN musi wrócić do kompilacji JIT. Z kolei platformy .NET Native tworzy tylko obrazów macierzystych i nie wrócił do kompilacji JIT. W związku z tym tylko metadane wymagane dla niektórych odbicia, serializacji i scenariusze międzyoperacyjne muszą zostać zachowane.  
  
-   NGEN nadal korzysta pełnego środowiska CLR dla usług, takich jak zestaw ładowania remoting, interop, zarządzania pamięcią, wyrzucanie elementów bezużytecznych i w razie potrzeby kompilacji JIT. W .NET Native wiele z tych usług są albo niepotrzebnych (kompilacja JIT) lub są rozwiązane w czasie kompilacji i włączyć w zestawie aplikacji. Pozostałych usług, których najważniejszy jest wyrzucanie elementów bezużytecznych, znajdują się w środowisku uruchomieniowym znacznie mniejszy, refaktoryzowane o nazwie mrt100_app.dll.  
  
-   Zwykle obrazów NGEN za słabe. Na przykład poprawki lub zmiana zależność zwykle wymaga zestawy, które go używają także ponowna błąd. Jest to szczególnie istotne, system zestawów w bibliotece klas programu .NET Framework. Z kolei platformy .NET Native umożliwia aplikacjom ma być obsługiwana niezależnie od siebie.  
  
## <a name="see-also"></a>Zobacz też  
 [Składniki samoopisujące się i metadane](../../../docs/standard/metadata-and-self-describing-components.md)  
 [Wewnątrz architektura .NET Native (klip wideo Channel 9)](http://channel9.msdn.com/Shows/Going+Deep/Inside-NET-Native)  
 [Odbicie i architektura .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)  
 [Ogólne wskazówki dotyczące rozwiązywania problemów z architekturą .NET Native](../../../docs/framework/net-native/net-native-general-troubleshooting.md)
