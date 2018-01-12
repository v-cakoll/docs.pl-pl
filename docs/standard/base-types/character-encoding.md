---
title: Znak kodowania w .NET
ms.custom: 
ms.date: 12/22/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encoding, understanding
- encoding, choosing
- encoding, fallback strategy
ms.assetid: bf6d9823-4c2d-48af-b280-919c5af66ae9
caps.latest.revision: "33"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: bf07665f0f7e79affd0b34b8faba94a56dd7d1d2
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="character-encoding-in-net"></a>Znak kodowania w .NET
Znaki to abstrakcyjna jednostek, które mogą być reprezentowane na wiele sposobów. Kodowanie znaków to system, który pary każdego znaku w obsługiwanych zestaw z niektórych wartość, która reprezentuje ten znak znaków. Na przykład Morse'a jest kodowania każdego znaku alfabetu łacińskiego z wzorcem kropek tej pary znaków i łączniki, które są odpowiednie do przesyłania za pośrednictwem telegraficznego wierszy. Kodowanie znaków dla pary komputerów dla każdego znaku zestaw z wartością numeryczną, która reprezentuje ten znak obsługiwanych znaków. Kodowanie znaków ma dwa różne składniki:  
  
-   Koder, który tłumaczy sekwencja znaków w sekwencji wartości liczbowych (w bajtach).  
  
-   Dekoder, który tłumaczy sekwencję bajtów w sekwencji znaków.  
  
 Kodowanie znaków w tym artykule opisano zasady, według których koder i dekoder działać. Na przykład <xref:System.Text.UTF8Encoding> klasa Opisuje reguły kodowanie i dekodowanie z 8-bitową przekształcania Format Unicode (UTF-8), który używa 1 do 4 bajty oznaczającego pojedynczy znak Unicode. Kodowania i dekodowania mogą również obejmować sprawdzania poprawności. Na przykład <xref:System.Text.UnicodeEncoding> klasa sprawdza wszystkie części znaku dwuskładnikowego, aby upewnić się, ponieważ stanowią one prawidłowe znaki dwuskładnikowe. (Para zastępcza składa się z znak z zakresu od U + D800 do U + DBFF następuje znak z zakresu od U + DC00 do U + DFFF punktem kodu punktem kodu).  Strategia rezerwowa określa sposób obsługi przez koder nieprawidłowe znaki lub jak dekodera obsługuje nieprawidłowe bajty.  
  
> [!WARNING]
>  Klasy kodowania platformy .NET umożliwiają przechowywanie i konwertowania danych znakowych. Powinny one nie służyć do przechowywania danych binarnych w postaci ciągu. W zależności od tego, czy kodowanie używane, konwertowania danych binarnych na ciąg format kodowania klasy mogą powodować nieoczekiwane zachowanie i utworzyć nieprawidłowe lub uszkodzone dane. Aby dane binarne w postaci ciągu, użyj <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> metody.  
  
 .NET używa kodowania UTF-16 (reprezentowane przez <xref:System.Text.UnicodeEncoding> klasy) do reprezentowania znaków i ciągów. Aplikacje kierowanych środowisko uruchomieniowe języka wspólnego używać koderów do mapowania oświadczenia znaków Unicode obsługiwanych przez środowisko uruchomieniowe języka wspólnego do innych systemów kodowania. Dekodery one służy do mapowania znaków kodowania Unicode z systemem innym niż Unicode.  
  
 Ten temat składa się z następujących sekcji:  
  
-   [Kodowanie w .NET](../../../docs/standard/base-types/character-encoding.md#Encodings)  
  
-   [Wybieranie klasy kodowania](../../../docs/standard/base-types/character-encoding.md#Selecting)  
  
-   [Przy użyciu kodowania obiektu](../../../docs/standard/base-types/character-encoding.md#Using)  
  
-   [Wybieranie strategii rezerwowej](../../../docs/standard/base-types/character-encoding.md#FallbackStrategy)  
  
-   [Implementowanie niestandardowych strategia rezerwowa](../../../docs/standard/base-types/character-encoding.md#Custom)  
  
<a name="Encodings"></a>   
## <a name="encodings-in-net"></a>Kodowanie w .NET  
 Wszystkich znaków kodowania klasy .NET dziedziczą w <xref:System.Text.Encoding?displayProperty=nameWithType> klasy, która jest klasą abstrakcyjną, który definiuje typowe funkcje do wszystkich znaków kodowania. Aby uzyskać dostęp do poszczególnych obiektów kodowania zaimplementowany w środowisku .NET, wykonaj następujące czynności:  
  
-   Użyj właściwości statycznej <xref:System.Text.Encoding> klasy, która zwraca obiekty reprezentujące kodowania znaków standardowych dostępnych w programie .NET (ASCII, UTF-7, UTF-8, UTF-16 i UTF-32). Na przykład <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> zwraca właściwość <xref:System.Text.UnicodeEncoding> obiektu. Każdy obiekt używa wymiany powrotu do obsługi ciągów, które go nie można zakodować i bajtów, których nie można go zdekodować. (Aby uzyskać więcej informacji, zobacz [powrotu zastępczy](../../../docs/standard/base-types/character-encoding.md#Replacement) sekcji.)  
  
-   Wywołanie kodowanie przez konstruktora klasy. W ten sposób można utworzyć wystąpienia elementu obiektów ASCII, UTF-7, UTF-8, UTF-16 i kodowania UTF-32. Domyślnie każdy obiekt używa zastępczy powrotu do obsługi ciągów, które go nie można zakodować i bajtów, których nie można go zdekodować, ale można określić, że powinno być wyjątek zamiast tego. (Aby uzyskać więcej informacji, zobacz [powrotu zastępczy](../../../docs/standard/base-types/character-encoding.md#Replacement) i [powrotu wyjątek](../../../docs/standard/base-types/character-encoding.md#Exception) sekcje.)  
  
-   Wywołanie <xref:System.Text.Encoding.%23ctor%28System.Int32%29?displayProperty=nameWithType> Konstruktor i przekaż go liczba całkowita, która reprezentuje kodowania. Standardowych obiektów kodowania Użyj powrotu zastąpienia i strona kodowa i zestaw znaków dwubajtowych (DBCS) kodowanie obiektów Użyj najlepszego dopasowania powrotu do dojścia ciągów, które nie mogą one kodowania i bajtów, które ich nie można zdekodować. (Aby uzyskać więcej informacji, zobacz [powrotu Best-Fit](../../../docs/standard/base-types/character-encoding.md#BestFit) sekcji.)  
  
-   Wywołanie <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> metodę, która zwraca wszystkie standardowe, strona kodowa lub kodowania znaków Dwubajtowych dostępnych w programie .NET. Przeciążenia pozwalają określić obiekt rezerwowy koder i dekoder.  
  
> [!NOTE]
>  Unicode Standard przypisuje punkt kodu (number) i nazwę każdego znaku w każdej obsługiwanej skryptu. Na przykład znak "A" jest reprezentowana przez punkt kodu U + 0041 i nazwie "ŁACIŃSKIEGO litera, A". Kodowanie Format transformacji Unicode (UTF) zdefiniuj sposoby kodowania tego punktu kodu do sekwencji bajtów co najmniej jeden. Schemat kodowania Unicode upraszcza projektowanie aplikacji gotowe, ponieważ zezwala ona na znaki z dowolnego zestawu być reprezentowane w jednym kodowania znaków. Deweloperzy aplikacji już nie mieć do śledzenia schemat kodowania, który został użyty do utworzenia znaków dla określonego języka lub zapisywanie systemu i danych mogą być współużytkowane przez systemy międzynarodowe nie są uszkodzone.  
>   
>  .NET obsługuje trzy rodzaje kodowania zdefiniowane w standardzie Unicode: UTF-8, UTF-16 i UTF-32. Aby uzyskać więcej informacji, patrz Unicode Standard na [strony głównej Unicode](http://www.unicode.org/).  
  
 Można pobrać informacji o kodowania dostępnych w programie .NET, wywołując <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> metody. .NET obsługuje zestaw znaków kodowania systemów wymienionych w poniższej tabeli.  
  
|Kodowanie|Class|Opis|Zalety i wady|  
|--------------|-----------|-----------------|-------------------------------|  
|ASCII|<xref:System.Text.ASCIIEncoding>|Koduje ograniczony zakres znaków za pomocą dolnej siedem bitów bajtu.|Ponieważ ten typ kodowania tylko obsługuje wartości znakowych z 0000 U + za pośrednictwem U + 007F, w większości przypadków jest nieodpowiedni dla aplikacji międzynarodowych.|  
|UTF-7|<xref:System.Text.UTF7Encoding>|Reprezentuje znaków jako sekwencję 7-bitowe znaki ASCII. Znaki spoza zestawu ASCII Unicode są reprezentowane przez sekwencja znaków ASCII.|UTF-7 obsługuje protokoły, takie jak wiadomości e-mail i grup dyskusyjnych protokołów. Jednak UTF-7 nie jest szczególnie bezpieczny i niezawodny. W niektórych przypadkach zmiana jeden bit może znacząco zmieniają interpretacji cały ciąg UTF-7. W pozostałych przypadkach różne ciągi UTF-7 może zakodować tego samego tekstu. Sekwencji, które zawierają znaki spoza zestawu ASCII wymaga więcej miejsca niż UTF-8, UTF-7 i kodowanie dekodowania jest wolniejsze. W związku z tym należy użyć UTF-8 zamiast UTF-7, jeśli to możliwe.|  
|UTF-8|<xref:System.Text.UTF8Encoding>|Reprezentuje każdy punkt kodu Unicode sekwencję bajtów 1 do 4.|UTF-8 obsługuje rozmiary danych 8-bitową i działa prawidłowo w przypadku wielu istniejących systemach operacyjnych. Dla zakresu znaków ASCII UTF-8 jest taki sam jak kodowanie ASCII i umożliwia szerszy zestaw znaków. Jednak skryptów chiński — japoński-koreańskich lub UTF-8 mogą wymagać trzech bajtów dla każdego znaku i może powodować większe rozmiary danych niż UTF-16. Należy pamiętać, czasami ilość danych ASCII, takich jak tagi HTML uzasadnia zwiększenie rozmiaru dla zakresu CJK.|  
|UTF-16|<xref:System.Text.UnicodeEncoding>|Reprezentuje każdy punkt kodu Unicode jako sekwencja jednego lub dwóch 16-bitowych liczb całkowitych. Najbardziej typowe znaków Unicode wymagają tylko jeden punkt kodu UTF-16, mimo że dodatkowych znaków Unicode (U + 10000 lub nowszej) wymaga dwóch punktów kodowych Surogat UTF-16. Obsługiwane są zarówno zamówień bajtów little endian i big-endian.|Środowisko uruchomieniowe języka wspólnego kodowania UTF-16 jest używana do reprezentowania <xref:System.Char> i <xref:System.String> wartości która jest używana do reprezentowania przez system operacyjny Windows `WCHAR` wartości.|  
|UTF-32.|<xref:System.Text.UTF32Encoding>|Reprezentuje każdy punkt kodu Unicode jako liczba całkowita 32-bitowych. Obsługiwane są zarówno zamówień bajtów little endian i big-endian.|Kodowanie UTF-32 jest używany, gdy aplikacje chce uniknąć zachowanie punktu kodu zastępczego w systemach operacyjnych, dla których za ważne jest zakodowany miejsca kodowania UTF-16. Pojedynczy symboli renderowania na ekranie nadal mogą być kodowane z więcej niż jednego znaku UTF-32.|  
|ANSI/ISO kodowania||Zapewnia obsługę szerokiej gamy stron kodowych. W systemach operacyjnych Windows stron kodowych są używane do obsługi określonego języka lub grupy języków. Aby uzyskać tabelę, która zawiera stron kodowych obsługiwany przez platformę .NET, zobacz <xref:System.Text.Encoding> klasy. Można pobrać kodowania obiekt strony kodowej określonego przez wywołanie metody <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> metody.|Strona kodowa zawiera 256 punktów kodu i jest liczony od zera. W większości stron kodowych punktów kodowych od 0 do 127 reprezentują zestaw znaków ASCII, a punktów kodowych 128 do 255 różnią się znacznie między stron kodowych. Na przykład strona kodowa 1252 przewiduje znaki Latin zapisywania systemy, w tym język angielski, niemiecki i francuski. Ostatnia strona kodowa 1252 punktów 128 kodu zawiera znaki akcentu. Strona kodowa 1253 zawiera kody znaków, które są wymagane w systemie grecki zapisu. Ostatni punktów 128 kodu w stronie kodowej 1253 zawierać grecki znaków. W związku z tym aplikacji, która opiera się na stronach kodowych ANSI nie można przechowywać grecki i niemieckim w strumieniu tekstu chyba, że zawiera on identyfikatora, który wskazuje stronę kodową do którego istnieje odwołanie.|  
|Zestaw znaków dwubajtowych (DBCS) kodowania||Obsługuje języków, takich jak chińskim, japońskim i koreański, zawierające więcej niż 256 znaków. W zestawie DBCS pary punktów kodowych (dwubajtowe) reprezentuje każdego znaku. <xref:System.Text.Encoding.IsSingleByte%2A?displayProperty=nameWithType> Zwraca `false` dla kodowań znaków Dwubajtowych. Możesz pobrać obiekt kodowania DBCS określonego przez wywołanie metody <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> metody.|W zestawie DBCS pary punktów kodowych (dwubajtowe) reprezentuje każdego znaku. Aplikacja, obsługując DBCS danych, pierwszy bajt znaku zestawów znaków Dwubajtowych (bajtu) są przetwarzane w połączeniu z następującym natychmiast bajt. Ponieważ pojedyncza para punktów kodowych znaków dwubajtowych może reprezentować różne znaki w zależności od strony kodowej, ten schemat nadal nie zezwala na połączenie dwóch języków, takich jak japoński i chiński w strumieniu danych.|  
  
 Kodowanie te umożliwiają pracę z znaków Unicode, a także kodowania, które są najczęściej używane w przypadku starszych aplikacji. Ponadto można utworzyć niestandardowego kodowania, definiując klasę, która jest pochodną <xref:System.Text.Encoding> i przesłanianie jej elementów członkowskich.  
  
### <a name="platform-notes-includenetcoreincludesnet-core-mdmd"></a>Uwagi dotyczące platformy:[!INCLUDE[net_core](../../../includes/net-core-md.md)]  
 Domyślnie [!INCLUDE[net_core](../../../includes/net-core-md.md)] nie udostępnia żadnych kodowania strony kodu innych niż strona kodowa 28591 i kodowania Unicode, takie jak UTF-8 i UTF-16. Można jednak dodać kodowania strony kodu znaleziono w standardowej aplikacji systemu Windows .NET kierowanych do aplikacji. Aby uzyskać pełne informacje, zobacz <xref:System.Text.CodePagesEncodingProvider> tematu.  
  
<a name="Selecting"></a>   
## <a name="selecting-an-encoding-class"></a>Wybieranie klasy kodowania  
 Jeśli masz możliwość wyboru kodowanie do użycia przez aplikację, należy użyć kodowania Unicode najlepiej albo <xref:System.Text.UTF8Encoding> lub <xref:System.Text.UnicodeEncoding>. (.NET obsługuje również trzeci kodowanie Unicode, <xref:System.Text.UTF32Encoding>.)  
  
 Jeśli planujesz użyć kodowanie ASCII (<xref:System.Text.ASCIIEncoding>), wybierz <xref:System.Text.UTF8Encoding> zamiast tego. Dwa kodowania są identyczne dla zestawu znaków ASCII, ale <xref:System.Text.UTF8Encoding> ma następujące zalety:  
  
-   Może to oznaczać każdy znak Unicode, podczas gdy <xref:System.Text.ASCIIEncoding> obsługuje tylko znak Unicode wartości między U + 007F 0000 i U +.  
  
-   Umożliwia wykrywanie błędów i większe bezpieczeństwo.  
  
-   Została dostosowana do można tak szybko, jak to możliwe, a powinien być szybciej niż inne kodowanie. Nawet w przypadku zawartości, która jest całkowicie ASCII, operacje wykonywane z <xref:System.Text.UTF8Encoding> są szybsze niż operacje przeprowadzane przy użyciu <xref:System.Text.ASCIIEncoding>.  
  
 Należy rozważyć użycie <xref:System.Text.ASCIIEncoding> tylko dla starszej wersji aplikacji. Jednak nawet w przypadku starszych aplikacji <xref:System.Text.UTF8Encoding> może być lepszym rozwiązaniem w następujących sytuacjach (przy założeniu ustawień domyślnych):  
  
-   Jeśli aplikacja ma zawartość, która nie jest ściśle ASCII i koduje go z <xref:System.Text.ASCIIEncoding>, każdy znak spoza zestawu ASCII są kodowane jako znak zapytania (?). Jeśli następnie aplikacja dekoduje dane, informacje zostaną utracone.  
  
-   Jeśli aplikacja ma zawartość, która nie jest ściśle ASCII i koduje go z <xref:System.Text.UTF8Encoding>, wynik wydaje się niezrozumiałe, jeśli interpretowane jako ASCII. Jednak jeśli aplikacja używa dekodera UTF-8 zdekodować te dane, dane wykonuje pomyślnie podróż.  
  
 W aplikacji sieci web powinien odzwierciedlać znaków wysyłane do klienta w odpowiedzi na żądania sieci web, kodowanie, używany przez klienta. W większości przypadków należy ustawić <xref:System.Web.HttpResponse.ContentEncoding%2A?displayProperty=nameWithType> właściwości do wartości zwracanej przez <xref:System.Web.HttpRequest.ContentEncoding%2A?displayProperty=nameWithType> właściwości do wyświetlania tekstu w kodowaniu, że użytkownik oczekuje.  
  
<a name="Using"></a>   
## <a name="using-an-encoding-object"></a>Przy użyciu kodowania obiektu  
 Koder konwertuje ciąg znaków (najczęściej, znaków Unicode) do jego (bajty) odpowiednik numeryczny. Na przykład można użyć kodera ASCII można przekonwertować na ASCII znaków Unicode, dzięki czemu mogą być wyświetlane w konsoli. Aby dokonać konwersji, należy wywołać <xref:System.Text.Encoding.GetBytes%2A?displayProperty=nameWithType> metody. Jeśli chcesz określić liczbę bajtów są niezbędne do przechowywania kodowanych znaków przed wykonaniem kodowanie, należy wywołać <xref:System.Text.Encoding.GetByteCount%2A> metody.  
  
 W poniższym przykładzie użyto tablicy jednobajtowych do kodowania ciągów w dwóch osobnych operacji. Ta funkcja obsługuje indeksu, który wskazuje położenie początkowe w tablicy bajtowej dla następnego zestawu bajtów kodowany w formacie ASCII. Wywołuje <xref:System.Text.ASCIIEncoding.GetByteCount%28System.String%29?displayProperty=nameWithType> metody upewnij się, że tablica bajtów jest wystarczająco duży, aby zmieścił się w zaszyfrowanym ciągiem. Następnie wywołuje <xref:System.Text.ASCIIEncoding.GetBytes%28System.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Byte%5B%5D%2CSystem.Int32%29?displayProperty=nameWithType> do kodowania znaków w ciągu.  
  
 [!code-csharp[Conceptual.Encoding#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/getbytes1.cs#8)]
 [!code-vb[Conceptual.Encoding#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/getbytes1.vb#8)]  
  
 Dekoder konwertuje tablicę bajtów, które odzwierciedla określonego znaku kodowanie do zestawu znaków, albo w tablicy znaków w ciągu. Aby zdekodować tablicy bajtów do tablicy znaków, należy wywołać <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> metody. Aby zdekodować tablicy bajtowej na ciąg, należy wywołać <xref:System.Text.Encoding.GetString%2A> metody. Jeśli chcesz określić, ile znaków są niezbędne do przechowywania dekodowane bajtów przed wykonaniem dekodowanie, należy wywołać <xref:System.Text.Encoding.GetCharCount%2A> metody.  
  
 W poniższym przykładzie koduje trzy ciągi i dekoduje je do jednej tablicy znaków. Ta funkcja obsługuje wskazującą położenie początkowe w tablicy znaków dla następnego zestawu znaki dekodowane indeksu. Wywołuje <xref:System.Text.ASCIIEncoding.GetCharCount%2A> metody, aby upewnić się, że tablicy znaków jest wystarczająco duża, aby uwzględnić wszystkie znaki dekodowane. Następnie wywołuje <xref:System.Text.ASCIIEncoding.GetChars%28System.Byte%5B%5D%2CSystem.Int32%2CSystem.Int32%2CSystem.Char%5B%5D%2CSystem.Int32%29?displayProperty=nameWithType> metody zdekodować tablicy bajtów.  
  
 [!code-csharp[Conceptual.Encoding#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/getchars1.cs#9)]
 [!code-vb[Conceptual.Encoding#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/getchars1.vb#9)]  
  
 Kodowania i dekodowania metody klasy pochodzące z <xref:System.Text.Encoding> działają na pełny zestaw danych; oznacza to, wszystkie dane można lub dekodowanym jest dostarczany w wywołaniu pojedynczej metody. Jednak w niektórych przypadkach dane są dostępne w strumieniu, a dane można lub dekodowanym mogą być dostępne tylko z oddzielnych operacji odczytu. Wymaga to operację kodowania lub dekodowania do zapamiętania żadnego zapisanego stanu z poprzedniego wywołania. Metody klas pochodnych <xref:System.Text.Encoder> i <xref:System.Text.Decoder> są w stanie obsłużyć kodowania i dekodowania operacje obejmujące wiele wywołań metody.  
  
 <xref:System.Text.Encoder> Obiekt do określonego kodowania jest niedostępna z tym kodowania w <xref:System.Text.Encoding.GetEncoder%2A?displayProperty=nameWithType> właściwości. A <xref:System.Text.Decoder> obiekt do określonego kodowania jest niedostępna z tym kodowania w <xref:System.Text.Encoding.GetDecoder%2A?displayProperty=nameWithType> właściwości. Dekodowania operacji, należy pamiętać, że klasy wyprowadzone z <xref:System.Text.Decoder> obejmują <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> metody, ale nie ma metody, która odpowiada <xref:System.Text.Encoding.GetString%2A?displayProperty=nameWithType>.  
  
 Poniższy przykład przedstawia różnice między <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> i <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> metody dekodowania tablicy bajtów Unicode. Przykład koduje ciąg, który zawiera niektóre znaki Unicode w pliku, a następnie korzysta z dwóch metod dekodowania zdekodować ich dziesięć bajtów w czasie. Ponieważ para zastępcza występuje w bajtach dziesiątego i jedenastego, jest dekodowany w oddzielnych metodach wywołania. Jak pokazano na dane wyjściowe, <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> — metoda nie jest w stanie prawidłowo zdekodować bajtów i zamiast tego zastępuje je U + FFFD (znak zastępczy). Z drugiej strony <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> metoda jest w stanie pomyślnie zdekodować tablicy bajtów uzyskanie oryginalnego ciągu.  
  
 [!code-csharp[Conceptual.Encoding#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/stream1.cs#10)]
 [!code-vb[Conceptual.Encoding#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/stream1.vb#10)]  
  
<a name="FallbackStrategy"></a>   
## <a name="choosing-a-fallback-strategy"></a>Wybieranie strategii rezerwowej  
 Gdy metoda próbuje kodowania i dekodowania znak, ale nie istnieje żadne mapowanie, musi on implementować strategia rezerwowa, który określa sposób obsługi mapowania nie powiodło się. Istnieją trzy typy rezerwowy strategii:  
  
-   Rezerwa najlepszego dopasowania  
  
-   Zastąpienie rezerwowej  
  
-   Wyjątek rezerwowej  
  
> [!IMPORTANT]
>  Najczęściej występujących problemów podczas wykonywania operacji kodowania wystąpić, gdy znak Unicode nie można zamapować na stronę kodu określonego kodowania. Najbardziej typowe problemy w dekodowania operacji wystąpić, gdy nieprawidłowy bajt sekwencji nie można przetłumaczyć prawidłowych znaków Unicode. Z tego względu należy wiedzieć strategii rezerwowej, która korzysta z określonego obiektu kodowania. Jeśli to możliwe, należy określić strategia rezerwowa używane przez obiekt kodowania, gdy można utworzyć wystąpienia obiektu.  
  
<a name="BestFit"></a>   
### <a name="best-fit-fallback"></a>Rezerwa najlepszego dopasowania  
 Gdy znak nie ma dokładnego dopasowania w kodowaniu docelowej, koder spróbować mapowanie go na podobny znak. (Najlepszego dopasowania powrotu jest przeważnie kodowania zamiast dekodowania problem. Istnieje bardzo niewiele stron kodowych znaków, które nie mogą być pomyślnie zamapowany na Unicode.) Najlepszego dopasowania powrotu jest wartością domyślną stronę kodową i kodowania, które są pobierane przez zestaw znaków dwubajtowych <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> i <xref:System.Text.Encoding.GetEncoding%28System.String%29?displayProperty=nameWithType> przeciążenia.  
  
> [!NOTE]
>  Teoretycznie kodowanie Unicode klasy podana w .NET (<xref:System.Text.UTF8Encoding>, <xref:System.Text.UnicodeEncoding>, i <xref:System.Text.UTF32Encoding>) obsługuje każdy znak każdego zestawu znaków, więc można go użyć aby wyeliminować problemy rezerwowy najlepszego dopasowania.  
  
 Strategie najlepszego dopasowania różnią się inny kod stron. Na przykład Latin pełnej szerokości dla niektórych stron kodowych znaków mapy w celu częściej połówkowej szerokości znaki alfabetu łacińskiego. To mapowanie nie zostało utworzone dla innych stron kodowych. Nawet w przypadku aktywnego strategii najlepszego dopasowania nie ma żadnych imaginable nadające się do niektórych znaków w niektórych kodowania. Na przykład chiński ideogramów nie ma uzasadnione mapowania strona kodowa 1252. W takim przypadku służy ciąg zastępczy. Domyślnie ten ciąg jest tylko jeden znak zapytania (U + 003F).  
  
> [!NOTE]
>  Strategie najlepszego dopasowania nie opisano szczegółowo. Jednak kilka stron kodowych są udokumentowane w [konsorcjum Unicode](http://www.unicode.org/Public/MAPPINGS/VENDORS/MICSFT/WindowsBestFit/) witryny sieci Web. Zapoznaj się z tematem **readme.txt** plików w tym folderze opis sposobu interpretowania pliki mapowania.
  
 W poniższym przykładzie użyto strona kodowa 1252 (Windows strony kodowej dla języków zachodnich Europejskiego) w celu zilustrowania mapowanie najlepszego dopasowania i jego wady. <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> Metoda służy do pobierania kodowania obiekt strona kodowa 1252. Domyślnie używa mapowanie najlepszego dopasowania dla znaków Unicode, które nie obsługują. Przykład tworzy ciąg, który zawiera trzy z systemem innym niż znaki ASCII - KÓŁKU S litera ŁACIŃSKA (U + 24C 8), indeks GÓRNY PIĘĆ (U + 2075), a NIESKOŃCZONOŚCIĄ (U + 221E) - rozdzielone spacjami. Jak pokazano na dane wyjściowe z przykładu, gdy jest zakodowany ciąg, trzy znaki z systemem innym niż miejsce oryginalnego są zastępowane przez znak zapytania (U + 003F), PIĘCIU CYFR (U + 0035) i osiem CYFRĘ (U + 0038). 8 CYFR nie zastępuje szczególnie niską nieobsługiwany znak NIESKOŃCZONOŚCI, a znak zapytania oznacza, że mapowania dla nie była dostępna oryginalnego znaku.  
  
 [!code-csharp[Conceptual.Encoding#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1.cs#1)]
 [!code-vb[Conceptual.Encoding#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1.vb#1)]  
  
 Domyślnym zachowaniem jest mapowanie najlepszego dopasowania <xref:System.Text.Encoding> obiektu kodującej danych Unicode do danych strony kodu i istnieją starsze aplikacje korzystające z tego zachowania. Jednak większość nowych aplikacji należy unikać najlepszego dopasowania zachowanie ze względów bezpieczeństwa. Na przykład aplikacje nie należy umieszczać nazwy domeny za pomocą kodowania najlepszego dopasowania.  
  
> [!NOTE]
>  Można też wdrożyć niestandardowe mapowanie najlepszego dopasowania powrotu do kodowania. Aby uzyskać więcej informacji, zobacz [realizację strategii powrotu niestandardowe](../../../docs/standard/base-types/character-encoding.md#Custom) sekcji.  
  
 Jeśli najlepszego dopasowania powrotu jest ustawieniem domyślnym dla obiekt kodowania, możesz wybrać inny strategia rezerwowa podczas pobierania <xref:System.Text.Encoding> obiektu przez wywołanie metody <xref:System.Text.Encoding.GetEncoding%28System.Int32%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> lub <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> przeciążenia. Poniższa sekcja zawiera przykład zastępujący każdego znaku, które nie mogą być mapowane na strona kodowa 1252 gwiazdką (*).  
  
 [!code-csharp[Conceptual.Encoding#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1a.cs#3)]
 [!code-vb[Conceptual.Encoding#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1a.vb#3)]  
  
<a name="Replacement"></a>   
### <a name="replacement-fallback"></a>Zastąpienie powrotu  
 Gdy znak nie ma dokładnego dopasowania w systemie docelowym, ale nie nie odpowiedni znak, które mogą być mapowane na, aplikacji można określić znak zastępczy lub ciąg. Jest to domyślne zachowanie dla dekodera Unicode, który zastępuje wszelkie sekwencji dwubajtowego, która nie można go zdekodować REPLACEMENT_CHARACTER (U + FFFD). Istnieje również domyślne zachowanie <xref:System.Text.ASCIIEncoding> klasy, która zastępuje każdego znaku, który go nie kodowania i dekodowania znakiem zapytania. Poniższy przykład przedstawia zastąpienia znaków ciągu Unicode z poprzedniego przykładu. Jak pokazano na dane wyjściowe, nie można dekodować do wartości bajtu ASCII każdego znaku zastępuje 0x3F, czyli kodu ASCII znaku zapytania.  
  
 [!code-csharp[Conceptual.Encoding#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/replacementascii.cs#2)]
 [!code-vb[Conceptual.Encoding#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/replacementascii.vb#2)]  
  
 .NET zawiera <xref:System.Text.EncoderReplacementFallback> i <xref:System.Text.DecoderReplacementFallback> klasy, które zastępuje ciąg zastępczy, jeśli znak nie jest zmapowany w kodowania lub dekodowania operacji. Domyślnie ten ciąg zastępczy jest znak zapytania, ale można wywoływać przeciążenia konstruktora klasy, aby wybrać inny ciąg. Zazwyczaj ciąg zastępczy jest pojedynczym znakiem, ale nie jest wymagane. Poniższy przykład umożliwia zmianę zachowania kodera strona 1252 kodu przez utworzenie wystąpienia <xref:System.Text.EncoderReplacementFallback> obiekt, który używa znak gwiazdki (*) jako ciąg zastępczy.  
  
 [!code-csharp[Conceptual.Encoding#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1a.cs#3)]
 [!code-vb[Conceptual.Encoding#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1a.vb#3)]  
  
> [!NOTE]
>  Można też wdrożyć zastępczej klasie do kodowania. Aby uzyskać więcej informacji, zobacz [realizację strategii powrotu niestandardowe](../../../docs/standard/base-types/character-encoding.md#Custom) sekcji.  
  
 Oprócz znak zapytania (U + 003F) znak zastępczy Unicode (U + FFFD) to powszechnie używane jako ciąg zastępczy, zwłaszcza w przypadku dekodowania sekwencji bajtów, które nie można pomyślnie przetłumaczyć znaków Unicode. Jednak mogą wybrać dowolny ciąg zastępczy i może zawierać wielu znaków.  
  
<a name="Exception"></a>   
### <a name="exception-fallback"></a>Wyjątek powrotu  
 Zamiast udostępnianie najlepszego dopasowania rezerwowe lub ciąg zastępczy, może zgłosić kodera <xref:System.Text.EncoderFallbackException> , jeśli nie można zakodować zestawu znaków i może zgłosić dekodera <xref:System.Text.DecoderFallbackException> przypadku nie można zdekodować tablicy bajtów. Do zgłoszenia wyjątku w kodowania i dekodowania operacji, należy podać <xref:System.Text.EncoderExceptionFallback> obiektu i <xref:System.Text.DecoderExceptionFallback> obiektu, odpowiednio do <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> metody. Poniższy przykład przedstawia wyjątek powrotu z <xref:System.Text.ASCIIEncoding> klasy.  
  
 [!code-csharp[Conceptual.Encoding#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/exceptionascii.cs#4)]
 [!code-vb[Conceptual.Encoding#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/exceptionascii.vb#4)]  
  
> [!NOTE]
>  Można też wdrożyć program obsługi wyjątku niestandardowych operacji kodowania. Aby uzyskać więcej informacji, zobacz [realizację strategii powrotu niestandardowe](../../../docs/standard/base-types/character-encoding.md#Custom) sekcji.  
  
 <xref:System.Text.EncoderFallbackException> i <xref:System.Text.DecoderFallbackException> obiektów podaj następujące informacje o warunku, który spowodował wyjątek:  
  
-   <xref:System.Text.EncoderFallbackException> Obiekt zawiera <xref:System.Text.EncoderFallbackException.IsUnknownSurrogate%2A> metodę, która wskazuje, czy znak lub znaków, które nie może zostać zakodowany reprezentują para zastępcza Nieznany (w takim przypadku metoda zwraca `true`) lub nieznany pojedynczego znaku (w takiej sytuacji, metoda zwraca `false`). Znaki w para zastępcza są dostępne z <xref:System.Text.EncoderFallbackException.CharUnknownHigh%2A?displayProperty=nameWithType> i <xref:System.Text.EncoderFallbackException.CharUnknownLow%2A?displayProperty=nameWithType> właściwości. Nieznany pojedynczy znak jest dostępna z <xref:System.Text.EncoderFallbackException.CharUnknown%2A?displayProperty=nameWithType> właściwości. <xref:System.Text.EncoderFallbackException.Index%2A?displayProperty=nameWithType> Właściwość wskazuje pozycji w ciągu odnaleziono pierwszego znaku, który nie jest zaszyfrowana.  
  
-   <xref:System.Text.DecoderFallbackException> Obiekt zawiera <xref:System.Text.DecoderFallbackException.BytesUnknown%2A> właściwości, która zwraca tablicę bajtów, które nie mogą zostać zdekodowane. <xref:System.Text.DecoderFallbackException.Index%2A?displayProperty=nameWithType> Właściwość wskazuje pozycję początkową nieznany bajtów.  
  
 Mimo że <xref:System.Text.EncoderFallbackException> i <xref:System.Text.DecoderFallbackException> obiektów podaj odpowiednie informacje diagnostyczne o wyjątku, nie zapewniają dostęp do kodowania lub dekodowania buforu. W związku z tym nie zezwalają na nieprawidłowe dane do zastąpienia lub usunąć w metodzie kodowania lub dekodowania.  
  
<a name="Custom"></a>   
## <a name="implementing-a-custom-fallback-strategy"></a>Implementowanie niestandardowych strategia rezerwowa  
 Oprócz mapowanie najlepszego dopasowania implementowany wewnętrznie przez stron kodowych .NET zawiera następujące klasy wykonywania strategia rezerwowa:  
  
-   Użyj <xref:System.Text.EncoderReplacementFallback> i <xref:System.Text.EncoderReplacementFallbackBuffer> do zastąpienia znaków kodowania operacji.  
  
-   Użyj <xref:System.Text.DecoderReplacementFallback> i <xref:System.Text.DecoderReplacementFallbackBuffer> do zastąpienia znaków dekodowania operacji.  
  
-   Użyj <xref:System.Text.EncoderExceptionFallback> i <xref:System.Text.EncoderExceptionFallbackBuffer> wyrzucenie <xref:System.Text.EncoderFallbackException> gdy znak nie może zostać zakodowany.  
  
-   Użyj <xref:System.Text.DecoderExceptionFallback> i <xref:System.Text.DecoderExceptionFallbackBuffer> wyrzucenie <xref:System.Text.DecoderFallbackException> po znaku nie może zostać zdekodowane.  
  
 Ponadto można zaimplementować niestandardowe rozwiązania obejmującego powrotu najlepszego dopasowania, powrotu zastąpienia lub powrotu wyjątek, wykonaj następujące czynności:  
  
1.  Klasa wyprowadzona z <xref:System.Text.EncoderFallback> operacjach kodowania i z <xref:System.Text.DecoderFallback> dekodowania operacji.  
  
2.  Klasa wyprowadzona z <xref:System.Text.EncoderFallbackBuffer> operacjach kodowania i z <xref:System.Text.DecoderFallbackBuffer> dekodowania operacji.  
  
3.  Do wyjątków rezerwowej, gdy wstępnie zdefiniowane <xref:System.Text.EncoderFallbackException> i <xref:System.Text.DecoderFallbackException> klas nie spełnia Twoich potrzeb, takich jak wyprowadzenia klasy z obiektu wyjątek <xref:System.Exception> lub <xref:System.ArgumentException>.  
  
### <a name="deriving-from-encoderfallback-or-decoderfallback"></a>Wyprowadzanie z EncoderFallback lub DecoderFallback  
 Implementacji niestandardowego rozwiązania rezerwowej, należy utworzyć klasę, która dziedziczy <xref:System.Text.EncoderFallback> operacjach kodowania i z <xref:System.Text.DecoderFallback> dekodowania operacji. Wystąpieniami tych klas są przekazywane do <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> — metoda i służą jako pośrednik między klasą kodowania i rezerwowy implementacji.  
  
 Po utworzeniu niestandardowego rozwiązania rezerwowy koder i dekoder, musi implementować następujące elementy:  
  
-   <xref:System.Text.EncoderFallback.MaxCharCount%2A?displayProperty=nameWithType> Lub <xref:System.Text.DecoderFallback.MaxCharCount%2A?displayProperty=nameWithType> właściwość, która zwraca maksymalna dopuszczalna liczba znaków, które może rezerwowy najlepszego dopasowania, wymiana albo wyjątek wróć do Zamień jeden znak. Dla niestandardowego wyjątku rezerwowej jego wartość wynosi zero.  
  
-   <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> Lub <xref:System.Text.DecoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> metody, która zwraca niestandardowe <xref:System.Text.EncoderFallbackBuffer> lub <xref:System.Text.DecoderFallbackBuffer> implementacji. Metoda jest wywoływana przez koder po napotkaniu pierwszego znaku, który nie może pomyślnie kodowania lub dekoder po napotkaniu pierwszy bajt, która nie może zdekodować pomyślnie.  
  
### <a name="deriving-from-encoderfallbackbuffer-or-decoderfallbackbuffer"></a>Wyprowadzanie z EncoderFallbackBuffer lub DecoderFallbackBuffer  
 Implementacji niestandardowego rozwiązania rezerwowej, należy także utworzyć klasę, która dziedziczy <xref:System.Text.EncoderFallbackBuffer> operacjach kodowania i z <xref:System.Text.DecoderFallbackBuffer> dekodowania operacji. Wystąpieniami tych klas są zwracane przez <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A> metody <xref:System.Text.EncoderFallback> i <xref:System.Text.DecoderFallback> klasy. <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> Metoda jest wywoływana przez koder po napotkaniu pierwszego znaku, który nie jest w stanie do kodowania, i <xref:System.Text.DecoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> metoda jest wywoływana przez dekoder po napotkaniu jednego lub więcej bajtów, które nie jest w stanie zdekodować. <xref:System.Text.EncoderFallbackBuffer> i <xref:System.Text.DecoderFallbackBuffer> klasy dostarczyć implementację rezerwowego. Każde wystąpienie reprezentuje buforu, który zawiera znaki powrotu, które zastąpi znak, który nie może zostać zakodowany lub sekwencji bajtów, które nie mogą zostać zdekodowane.  
  
 Po utworzeniu niestandardowego rozwiązania rezerwowy koder i dekoder, musi implementować następujące elementy:  
  
-   <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> Lub <xref:System.Text.DecoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> metody. <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>jest wywoływana przez koder dostarczenie informacji o znak, który go nie można zakodować w buforze rezerwowym. Znak, który ma zostać zakodowany może być para zastępcza, tej metody jest przeciążona. Przeciążeniami jest przekazywany znak, który ma zostać zakodowany i jej indeks w ciągu. Drugi przeciążenia jest przekazywany surogatu wysoki i niski, wraz z jej indeks w ciągu. <xref:System.Text.DecoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> Metoda jest wywoływana przez dekodera dostarczenie informacji o liczbę bajtów, które nie można go zdekodować buforze rezerwowym. Ta metoda jest przekazywana tablicę bajtów, które nie można go zdekodować, wraz z indeks pierwszego bajtu. Metoda rezerwowy powinna zwrócić `true` Jeśli buforze rezerwowym można podać najlepszego dopasowania lub znak zastępczy lub znaków; w przeciwnym razie powinien on zwrócić `false`. Wyjątek rezerwowy metodą rezerwową powinien zgłosić wyjątek.  
  
-   <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> Lub <xref:System.Text.DecoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> metodę, która jest wywoływana wielokrotnie przez koder lub dekodera do pobrania następnej znak w buforze rezerwowym. Gdy wszystkie znaki powrotu zostały zwrócone, metoda powinna zwrócić 0000 U +.  
  
-   <xref:System.Text.EncoderFallbackBuffer.Remaining%2A?displayProperty=nameWithType> Lub <xref:System.Text.DecoderFallbackBuffer.Remaining%2A?displayProperty=nameWithType> właściwość, która zwraca liczbę pozostałych znaków w buforze rezerwowym.  
  
-   <xref:System.Text.EncoderFallbackBuffer.MovePrevious%2A?displayProperty=nameWithType> Lub <xref:System.Text.DecoderFallbackBuffer.MovePrevious%2A?displayProperty=nameWithType> metodę, która przenosi bieżącą pozycję w buforze rezerwowym poprzedni znak.  
  
-   <xref:System.Text.EncoderFallbackBuffer.Reset%2A?displayProperty=nameWithType> Lub <xref:System.Text.DecoderFallbackBuffer.Reset%2A?displayProperty=nameWithType> metodę, która ponownie inicjuje buforze rezerwowym.  
  
 W przypadku powrotu najlepszego dopasowania lub rezerwowe zastępczy rezerwowy implementacja klas pochodnych <xref:System.Text.EncoderFallbackBuffer> i <xref:System.Text.DecoderFallbackBuffer> również obsługa dwa pola wystąpienia prywatnych: Dokładna liczba znaków w buforze; i indeks następny znak bufor do zwrócenia.  
  
### <a name="an-encoderfallback-example"></a>Przykład EncoderFallback  
 Wcześniejszego przykładu używany zastępczy powrotu do zastępowania znaków Unicode, który nie odpowiada na znaki ASCII gwiazdką (*). W poniższym przykładzie użyto implementacja niestandardowa rezerwowy najlepszego dopasowania zamiast zapewnienie lepszego mapowania znaki spoza zestawu ASCII.  
  
 Poniższy kod definiuje klasę o nazwie `CustomMapper` która jest pochodną <xref:System.Text.EncoderFallback> do obsługi mapowanie najlepszego dopasowania znaków innych niż ASCII. Jego `CreateFallbackBuffer` metoda zwraca `CustomMapperFallbackBuffer` obiektu, który zawiera <xref:System.Text.EncoderFallbackBuffer> implementacji. `CustomMapper` Klasy używa <xref:System.Collections.Generic.Dictionary%602> obiekt, aby zapisać mapowania nieobsługiwane znaki Unicode (wartość klucza) oraz ich odpowiednich znaków 8-bitową (które są przechowywane w dwóch kolejnych bajtów w 64-bitowa liczba całkowita). Aby udostępnić tego mapowania buforze rezerwowym `CustomMapper` wystąpienia jest przekazywana jako parametr `CustomMapperFallbackBuffer` konstruktora klasy. Ponieważ najdłuższym mapowania jest ciąg "INF" dla znaku Unicode U + 221E, `MaxCharCount` właściwość zwraca wartość 3.  
  
 [!code-csharp[Conceptual.Encoding#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#5)]
 [!code-vb[Conceptual.Encoding#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#5)]  
  
 Poniższy kod definiuje `CustomMapperFallbackBuffer` klasy, która jest pochodną <xref:System.Text.EncoderFallbackBuffer>. Słownik zawierający mapowanie najlepszego dopasowania i który jest zdefiniowany w `CustomMapper` wystąpienia jest dostępna z jego konstruktora klasy. Jego `Fallback` metoda zwraca `true` czy znaków Unicode, których nie można zakodować kodera ASCII są zdefiniowane w słowniku mapowania; w przeciwnym razie zwraca `false`. Dla każdego powrotu prywatna `count` zmienna oznacza liczbę znaków, która ma zostać zwrócone i prywatnych `index` zmiennej wskazuje pozycję buforu ciągów `charsToReturn`, z następny znak do zwrócenia.  
  
 [!code-csharp[Conceptual.Encoding#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#6)]
 [!code-vb[Conceptual.Encoding#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#6)]  
  
 Poniższy kod tworzy następnie wystąpienie `CustomMapper` obiektu i przekazuje ją do wystąpienia <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> metody. Dane wyjściowe wskazują, że najlepszego dopasowania implementacji rezerwowy pomyślnie obsługuje trzy znaki spoza zestawu ASCII w oryginalnym ciągu.  
  
 [!code-csharp[Conceptual.Encoding#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#7)]
 [!code-vb[Conceptual.Encoding#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#7)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Text.Encoder>  
 <xref:System.Text.Decoder>  
 <xref:System.Text.DecoderFallback>  
 <xref:System.Text.Encoding>  
 <xref:System.Text.EncoderFallback>  
 [Globalizacja i lokalizacja](../../../docs/standard/globalization-localization/index.md)
