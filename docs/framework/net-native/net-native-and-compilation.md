---
title: Architektura .NET Native i kompilacja
ms.date: 03/30/2017
ms.assetid: e38ae4f3-3e3d-42c3-a4b8-db1aa9d84f85
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a89474ddfe3bcde1c44271818b7e3c730469f48
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199711"
---
# <a name="net-native-and-compilation"></a>Architektura .NET Native i kompilacja
Aplikacje Windows 8.1 i Windows Desktop aplikacji, przeznaczonych dla środowiska.NET Framework są zapisywane w danym języku programowania i kompilowane do języka pośredniego (IL). W czasie wykonywania kompilator just-in-time (JIT) jest odpowiedzialny za kompilowanie IL do kodu natywnego dla komputera lokalnego, po prostu, zanim metoda jest wykonywana po raz pierwszy. Z kolei łańcucha narzędzi .NET Native konwertuje kod źródłowy do kodu natywnego w czasie kompilacji. W tym temacie porównano .NET Native z innymi technologiami kompilacji dostępne dla aplikacji .NET Framework oraz również zawiera omówienie praktyczne jak .NET Native generuje kodu natywnego, które mogą ułatwić zrozumienie, dlaczego wyjątków, które występują w kodzie są kompilowane przy użyciu platformy .NET Natywne nie występują w kod kompilowany dokładnie na czas.  
  
## <a name="net-native-generating-native-binaries"></a>Architektura .NET native: Generowanie natywnych plików binarnych  
 Czy obiektów docelowych programu .NET Framework i nie jest kompilowany przy użyciu łańcucha narzędzi .NET Native aplikacji składa się z zestawu aplikacji, w którym znajdują się następujące:  
  
-   [Metadane](../../../docs/standard/metadata-and-self-describing-components.md) opisujący zestaw, jego zależności, typów, zawiera i ich elementów członkowskich. Metadane są używane odbicia i dostęp z późnym wiązaniem i w niektórych przypadkach przez narzędzia kompilatora i tworzenia.  
  
-   W kodzie. Ten krok składa się z rozkazów języka pośredniego (IL). W czasie wykonywania kompilator just-in-time (JIT) tłumaczy to kod natywny dla platformy docelowej.  
  
 Oprócz z głównym zestawem aplikacji aplikacji wymaga następujących obecne:  
  
-   Dodatkowe biblioteki klas lub zestawów innych firm, które są wymagane przez aplikację. Zestawy te obejmują podobnie metadane opisujące zestaw, jego typy i składowe, a także IL, który implementuje wszystkie elementy członkowskie typu.  
  
-   Biblioteki klas programu .NET Framework. Jest to zbiór zestawów, który jest zainstalowany w systemie lokalnym za pomocą instalacji programu .NET Framework. Zestawy zawarte w bibliotece klas programu .NET Framework obejmują kompletny zestaw metadanych i wykonania kodu.  
  
-   Środowisko uruchomieniowe języka wspólnego. To zbiór biblioteki dołączanej dynamicznie, wykonujących takich usług jak ładowanie zestawu, kolekcji zarządzania i odzyskiwanie pamięci, obsługi wyjątków, kompilacja just-in-time, komunikacji zdalnej i współdziałania. Podobnie jak biblioteka klas środowiska uruchomieniowego jest zainstalowany w systemie lokalnym jako część instalacji programu .NET Framework.  
  
 Należy pamiętać, że całe środowisko uruchomieniowe języka wspólnego, a także metadanych i IL dla wszystkich typów w zestawach specyficzne dla aplikacji, zestawów innych firm i zestawy systemowe, musi być stosowany w przypadku aplikacji, aby zostać pomyślnie uruchomiony.  
  
## <a name="net-native-and-just-in-time-compilation"></a>Kompilacja .NET native i just-in-time  
 Dane wejściowe dla platformy .NET Native łańcucha narzędzi jest Windows przechowywać aplikację utworzoną przez C# lub kompilator Visual Basic. Innymi słowy łańcucha narzędzi .NET Native rozpoczyna wykonywanie, gdy kompilator języka zakończył kompilacji aplikacji Windows Store.  
  
> [!TIP]
>  Ponieważ dane wejściowe .NET Native IL i metadanymi zapisywanymi w zestawy zarządzane, można wciąż wykonywać generacji kod niestandardowy lub inne operacje niestandardowe przy użyciu zdarzenia sprzed kompilacji lub po kompilacji lub modyfikując plik projektu programu MSBuild.  
>   
>  Kategorie narzędzia, które modyfikują IL i tym samym zapobiec łańcucha narzędzi .NET analizowanie IL aplikacji nie są obsługiwane. Obfuscators są najbardziej istotnych narzędzi tego typu.  
  
 W trakcie konwersji aplikację z IL do kodu macierzystego, łańcucha narzędzi .NET Native wykonuje operacje, jak pokazano poniżej:  
  
-   W przypadku niektórych ścieżek kodu zastępuje kod, który opiera się na odbicia i metadanych z kodem natywnym statyczne. Na przykład, jeśli typ wartości nie powoduje zastąpienia <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> metody testu domyślne pod kątem równości używa odbicia do pobrania <xref:System.Reflection.FieldInfo> obiekty reprezentujące typ wartości pól, następnie porównuje wartości pól z dwóch wystąpień. Podczas kompilowania kodu do kodu macierzystego, łańcucha narzędzi .NET Native zamienia odbicia kodu i metadane statyczne porównania wartości pola.  
  
-   W przypadku, gdy jest to możliwe, podejmie próbę usunięcia wszystkich metadanych.  
  
-   Obejmuje w zestawach ostatecznej aplikacji kod implementacji, które faktycznie jest wywoływane przez aplikację. Dotyczy to zwłaszcza kodu w innych bibliotekach oraz w bibliotece klas programu .NET Framework. W rezultacie aplikacja nie jest już zależy od bibliotek innych firm lub pełnej biblioteki klas .NET Framework; Zamiast tego kodu w innych firm oraz biblioteki klas .NET Framework jest teraz lokalne dla aplikacji.  
  
-   Zastępuje pełnego środowiska CLR wycofanej środowiska uruchomieniowego, które zawiera moduł odśmiecania pamięci. Wycofanej środowisko uruchomieniowe znajduje się w bibliotece o nazwie mrt100_app.dll jest lokalna dla aplikacji, która jest tylko kilku kilobajtów kilkuset rozmiaru. Jest to możliwe, ponieważ łączenie statyczne eliminuje potrzebę stosowania wielu usług, wykonywane przez środowisko uruchomieniowe języka wspólnego.  
  
    > [!NOTE]
    >  .NET native używa tego samego modułu odśmiecania pamięci jako standardowe środowisko uruchomieniowe języka wspólnego. W moduł odśmiecania pamięci platformy .NET Native wyrzucania elementów bezużytecznych w tle jest włączona domyślnie. Aby uzyskać więcej informacji dotyczących wyrzucania elementów bezużytecznych, zobacz [podstawowe informacje dotyczące wyrzucania elementów bezużytecznych](../../../docs/standard/garbage-collection/fundamentals.md).  
  
> [!IMPORTANT]
>  .NET native kompiluje całej aplikacji do natywnej aplikacji. Nie zezwalaj można skompilować w jednym zestawie, który zawiera bibliotekę klas do kodu macierzystego, dlatego może zostać wywołana w niezależnie z kodu zarządzanego.  
  
 Wynikowa aplikacja, który jest wytwarzany przez łańcuch narzędzi .NET Native jest zapisywany w katalogu o nazwie ilc.out w katalogu debugowania lub wydania w katalogu projektu. Składa się z następujących plików:  
  
-   *\<nazwa_aplikacji >*.exe, wycinka plik wykonywalny, który po prostu transfery kontrolę specjalny `Main` wyeksportować w  *\<nazwa_aplikacji >*.dll.  
  
-   *\<Nazwa aplikacji >* dll, Windows dynamic połączyć bibliotekę, która zawiera kod aplikacji, a także kod od biblioteki klas programu .NET Framework i dowolnego bibliotek innych firm, które mają zależności na.  Zawiera także kod pomocy technicznej, takie jak kod wymagany do współdziałania z usługami Windows i serializacji obiektów w aplikacji.  
  
-   mrt100_app.dll, wycofanej środowiska uruchomieniowego, które udostępnia usługi czasu wykonywania, takie jak wyrzucanie elementów bezużytecznych.  
  
 Wszystkie zależności są przechwytywane przez manifest pakietu APPX aplikacji.  Oprócz aplikacji exe, dll i mrt100_app.dll, które są połączone bezpośrednio w pakiecie appx obejmuje to dwa pliki więcej:  
  
-   msvcr140_app.dll, biblioteki wykonawczej (CRT) C, które są używane przez mrt100_app.dll. Znajduje się odwołanie framework w pakiecie.  
  
-   mrt100.dll. Ta biblioteka zawiera funkcje, które może poprawić wydajność mrt100_app.dll, mimo że jego nieobecności nie uniemożliwia działania mrt100_app.dll. Jest on ładowany z katalogu system32 na komputerze lokalnym, jeśli jest obecny.  
  
 Ponieważ łańcucha narzędzi .NET Native łączy kod implementacji w swojej aplikacji, tylko wtedy, gdy wiadomo, że aplikacja faktycznie wywołuje kod, metadanych lub kod implementacji wymagane w następujących scenariuszach może być dołączone do Twojej aplikacji:  
  
-   Odbicia.  
  
-   Wywołanie dynamicznego lub z późnym wiązaniem.  
  
-   Serializacji i deserializacji.  
  
-   Usługa międzyoperacyjna modelu COM.  
  
 Jeśli wymagany kod metadanych lub implementacja jest nieobecne w czasie wykonywania, zgłasza wyjątek, środowisko uruchomieniowe platformy .NET Native. Można uniknąć tych wyjątków i upewnij się, że łańcucha narzędzi .NET Native zawiera wymagane metadane i wykonania kodu, przy użyciu [plik dyrektywy środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md), plik XML, który wyznacza metadane, którego elementy programu lub kod implementacji, muszą być dostępne w czasie wykonywania i przypisuje zasad wykonywania. Poniżej znajduje się domyślny plik dyrektywy środowiska uruchomieniowego, który jest dodawany do projektu Windows Store, który jest kompilowany przez łańcuch narzędzi .NET Native:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
  </Application>  
</Directives>  
```  
  
 Dzięki temu wszystkie typy, a także wszystkich jej członków z wszystkich zestawów w pakiecie app odbicia i dynamicznym wywołaniu. Jednak nie uwzględnia odbicia lub dynamicznej aktywacji typów w zestawach biblioteki klas .NET Framework. W wielu przypadkach jest to odpowiednie.  
  
## <a name="net-native-and-ngen"></a>Architektura .NET native i NGEN  
 [(Generator obrazu natywnego](../../../docs/framework/tools/ngen-exe-native-image-generator.md) (NGEN) kompiluje zestawy do kodu macierzystego i instaluje je w pamięci podręcznej obrazów natywnych na komputerze lokalnym. Jednak mimo że NGEN, takich jak .NET Native generuje kod natywny, różni się od platformy .NET Native pod pewnymi względami znaczące:  
  
-   Jeśli nie obrazów natywnych jest dostępny dla konkretnej metody, NGEN powraca do JITing kodu. Oznacza to, że obrazy natywne muszą w dalszym ciągu obejmują IL i metadanych, w przypadku, gdy NGEN musi przełączyć się na kompilację JIT. Z kolei .NET Native generuje wyłącznie obrazy natywne i nie wrócił do kompilacji JIT. W rezultacie tylko metadane wymagane dla niektórych odbicia, serializacja i międzyoperacyjne scenariuszy muszą być chronione.  
  
-   NGEN w dalszym ciągu zależą od środowiska uruchomieniowego języka wspólnego pełnej dla usług, takich jak ładowanie komunikacji zdalnej, Usługa międzyoperacyjna, zarządzanie pamięcią, wyrzucanie elementów bezużytecznych zestawu i, jeśli to konieczne, kompilacja JIT. W .NET Native wiele z tych usług są albo niepotrzebne (kompilacja JIT) lub są rozwiązane w czasie kompilacji i włączyć w zestawie aplikacji. Pozostałych usług, najważniejsze z nich jest wyrzucania elementów bezużytecznych, są uwzględnione w środowisku uruchomieniowym znacznie mniejszy, wycofanej o nazwie mrt100_app.dll.  
  
-   Zwykle obrazów NGEN za słabe. Na przykład poprawki lub zmiany zależność zwykle wymaga zestawów, które go używają również wystąpił ponownie. Dotyczy to zwłaszcza zestawów system w bibliotece klas programu .NET Framework. Z kolei .NET Native umożliwia aplikacjom, które ma zostać dostarczony niezależnie od siebie nawzajem.  
  
## <a name="see-also"></a>Zobacz też  
 [Składniki samoopisujące się i metadane](../../../docs/standard/metadata-and-self-describing-components.md)  
 [W obrębie architektury .NET Native (wideo Channel 9)](https://channel9.msdn.com/Shows/Going+Deep/Inside-NET-Native)  
 [Odbicie i architektura .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)  
 [Ogólne wskazówki dotyczące rozwiązywania problemów z architekturą .NET Native](../../../docs/framework/net-native/net-native-general-troubleshooting.md)
