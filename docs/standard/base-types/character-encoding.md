---
title: Kodowanie znaków w programie .NET
description: Więcej informacji na temat znaków kodowania i dekodowania na platformie .NET.
ms.date: 12/22/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encoding, understanding
- encoding, choosing
- encoding, fallback strategy
ms.assetid: bf6d9823-4c2d-48af-b280-919c5af66ae9
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: e8edc747c003cd5527df509af83325816671ddfb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59346109"
---
# <a name="character-encoding-in-net"></a>Kodowanie znaków w programie .NET
Znaki są abstrakcyjne jednostek, które mogą być przedstawione na wiele różnych sposobów. Kodowanie znaków to system, który pary, każdy znak w obsługiwanych znaków, zestaw z jakąś wartość, która reprezentuje ten znak. Na przykład Morse'a jest znakiem kodowania tej pary każdego znaku w alfabetu łacińskiego z wzorcem kropki i łączniki, które są odpowiednie na potrzeby transmisji przez telegraficznego wierszy. Kodowanie znaków dla pary komputerów dla każdego znaku obsługiwany zestaw z wartością liczbową, który reprezentuje ten znak znaków. Kodowanie znaków ma dwa różne składniki:  
  
-   Koder, który tłumaczy sekwencji znaków do sekwencji wartości liczbowych (w bajtach).  
  
-   Dekoder, który tłumaczy sekwencję bajtów do sekwencji znaków.  
  
 Kodowanie znaków w tym artykule opisano zasady, według których koder i dekoder działać. Na przykład <xref:System.Text.UTF8Encoding> klasy w tym artykule opisano zasady kodowanie i dekodowanie z 8-bitową przekształcania formatu Unicode (UTF-8), który używa jednej do czterech bajtach oznaczającego pojedynczy znak Unicode. Kodowanie i dekodowanie mogą również obejmować sprawdzania poprawności. Na przykład <xref:System.Text.UnicodeEncoding> klasa sprawdza wszystkie surogaty, aby upewnić się, ponieważ stanowią one prawidłowe znaki dwuskładnikowe. (Para zastępcza składa się z znakiem z zakresu od U + D800 do U + DBFF następuje znak z punktem kodu z zakresu od U + DC00 do U + DFFF punktu kodu).  Strategia rezerwowa określa sposób obsługi przez koder nieprawidłowe znaki lub jak dekodera obsługuje nieprawidłowe bajty.  
  
> [!WARNING]
>  Klasy kodowania platformy .NET umożliwiają przechowywanie i konwertowania danych znakowych. Nie powinny one używane do przechowywania danych binarnych w postaci ciągu. W zależności od kodowanie używane, konwersja danych binarnych na ciąg formatu przy użyciu klas kodowania można wprowadzić nieoczekiwane zachowanie i tworzenia nieprawidłowe lub uszkodzone dane. Aby przekonwertować danych binarnych w postaci ciągu, należy użyć <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> metody.  
  
 .NET używa kodowania UTF-16 (reprezentowane przez <xref:System.Text.UnicodeEncoding> klasy) do reprezentowania znaków i ciągów. Aplikacje przeznaczone środowiska uruchomieniowego języka wspólnego Użyj koderów, aby zamapować reprezentacji znaków Unicode obsługiwanych przez środowisko uruchomieniowe języka wspólnego do innych systemów kodowania. Dekodery one służy do mapowania znaków z innego niż Unicode kodowania na Unicode.  
  
 Ten temat zawiera następujące sekcje:  
  
-   [Kodowanie na platformie .NET](../../../docs/standard/base-types/character-encoding.md#Encodings)  
  
-   [Wybieranie klasy kodowania](../../../docs/standard/base-types/character-encoding.md#Selecting)  
  
-   [Używanie obiektu kodowania](../../../docs/standard/base-types/character-encoding.md#Using)  
  
-   [Wybieranie strategii rezerwowe](../../../docs/standard/base-types/character-encoding.md#FallbackStrategy)  
  
-   [Implementowanie niestandardowego strategia rezerwowa](../../../docs/standard/base-types/character-encoding.md#Custom)  
  
<a name="Encodings"></a>   
## <a name="encodings-in-net"></a>Kodowanie na platformie .NET  
 Wszystkich znaków kodowania klasy .NET dziedziczą w <xref:System.Text.Encoding?displayProperty=nameWithType> klasy, która jest klasą abstrakcyjną, definiujący funkcje wspólne do wszystkich znaków kodowania. Można uzyskać dostęp do poszczególnych obiektów kodowania zaimplementowany w środowisku .NET, wykonaj następujące czynności:  
  
-   Użyj właściwości statycznej <xref:System.Text.Encoding> klasy, która zwraca obiekty reprezentujące kodowania znaków standardowych dostępnych w programie .NET (ASCII, UTF-7, UTF-8, UTF-16 i UTF-32). Na przykład <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> właściwość zwraca <xref:System.Text.UnicodeEncoding> obiektu. Każdy obiekt używa zastąpienie rezerwowego ciągów uchwytu, które go nie można zakodować i bajtów, które nie można go zdekodować. (Aby uzyskać więcej informacji, zobacz [rezerwowe zastąpienie](../../../docs/standard/base-types/character-encoding.md#Replacement) sekcji.)  
  
-   Wywoływanie konstruktora klasy kodowania firmy. Obiekty ASCII, UTF-7, UTF-8, UTF-16 i UTF-32 kodowania mogą być utworzone w ten sposób. Domyślnie każdy obiekt używa zastąpienie rezerwowego do obsługi ciągów, które go nie można zakodować i bajtów, których nie można go zdekodować, ale można określić, czy należy zgłosić wyjątek zamiast tego. (Aby uzyskać więcej informacji, zobacz [rezerwowe zastąpienie](../../../docs/standard/base-types/character-encoding.md#Replacement) i [rezerwowe wyjątek](../../../docs/standard/base-types/character-encoding.md#Exception) sekcje.)  
  
-   Wywołaj <xref:System.Text.Encoding.%23ctor%28System.Int32%29?displayProperty=nameWithType> Konstruktor i przekazywanie ich liczba całkowita, która reprezentuje kodowania. Standard kodowania obiektów użyj rezerwowe zastąpienia i stronę kodową i zestaw znaków dwubajtowych (DBCS) kodowanie obiektów Użyj najlepszego dopasowania powrotu do ciągów uchwytu, które ich nie można zakodować i bajtów, które ich nie można zdekodować. (Aby uzyskać więcej informacji, zobacz [rezerwowe Best-Fit](../../../docs/standard/base-types/character-encoding.md#BestFit) sekcji.)  
  
-   Wywołaj <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> metody, która zwraca wszystkie standardowe, stronę kodową lub kodowanie znaków Dwubajtowych dostępne na platformie .NET. Przeciążenia pozwalają określać rezerwowego obiektu dla koder i dekoder.  
  
> [!NOTE]
>  Unicode Standard przypisuje punkt kodowy (liczba) i nazwę każdego znaku w każdej obsługiwanej skryptu. Na przykład znak "A" jest reprezentowany przez punkt kodowy U + 0041 i nazwie "LATIN CAPITAL LETTER A". Kodowania Format przekształcenia Unicode (UTF) zdefiniuj sposoby kodowanie tego punktu kodu do sekwencji bajtów jednego lub więcej. Schemat kodowania Unicode upraszcza opracowywanie aplikacji gotowej dla całego świata, ponieważ zezwala ona na znaki z dowolnego zestawu może być reprezentowana w jednym kodowania znaków. Deweloperzy aplikacji nie ma już do śledzenia schemat kodowania, który został użyty do utworzenia znaków dla określonego języka lub zapis systemu, a dane mogą być udostępniane między systemami w wielu krajach bez jest uszkodzony.  
>   
>  .NET obsługuje trzy rodzaje kodowania zdefiniowane w standardzie Unicode standard: UTF-8, UTF-16 i UTF-32. Aby uzyskać więcej informacji, zobacz Unicode Standard na [strony głównej Unicode](https://www.unicode.org/).  
  
 Można pobrać informacji na temat kodowania dostępne na platformie .NET, wywołując <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> metody. .NET wspomaga znaków kodowania systemów wymienionych w poniższej tabeli.  
  
|Kodowanie|Class|Opis|Zalety i wady|  
|--------------|-----------|-----------------|-------------------------------|  
|ASCII|<xref:System.Text.ASCIIEncoding>|Koduje ograniczony zakres znaków przy użyciu niższe siedem bitów bajtu.|Ponieważ to kodowanie tylko obsługuje wartości znakowych z 0000 U + poprzez U + 007F, w większości przypadków jest to niewystarczające do aplikacji międzynarodowych.|  
|UTF-7|<xref:System.Text.UTF7Encoding>|Reprezentuje znaków jako sekwencje znaków ASCII 7-bitowego. Znaki spoza zestawu ASCII Unicode są reprezentowane przez sekwencję unikową znaków ASCII.|UTF-7 obsługuje protokoły, takie jak wiadomości e-mail i protokoły grupy dyskusyjnej. Jednakże UTF-7 nie jest szczególnie bezpieczne i niezawodne. W niektórych przypadkach zmieniając jeden bit może znacząco zmieniają interpretacji cały ciąg UTF-7. W innych przypadkach różne ciągi UTF-7 można zakodować ten sam tekst. Sekwencje, które zawierają znaki spoza zestawu ASCII wymaga więcej miejsca niż UTF-8, UTF-7 i Kodowanie dekodowanie jest wolniejsze. W związku z tym należy użyć UTF-8 zamiast UTF-7, jeśli jest to możliwe.|  
|UTF-8|<xref:System.Text.UTF8Encoding>|Reprezentuje każdy punkt kodu Unicode jako sekwencja jednej do czterech bajtów.|UTF-8 obsługuje ilości danych 8-bitową i dobrze działa z wielu istniejących systemach operacyjnych. Dla zakresu znaków ASCII UTF-8 jest taka sama jak kodowanie ASCII i zezwala na szerszy zestaw znaków. Jednak dla skryptów chiński — japoński — koreańskich lub UTF-8 mogą wymagać trzy bajty dla każdego znaku i może powodować większe ilości danych niż UTF-16. Należy pamiętać, czasami ilość danych ASCII, takich jak tagi HTML uzasadnia zwiększony rozmiar dla zakresu CJK.|  
|UTF-16|<xref:System.Text.UnicodeEncoding>|Reprezentuje każdy punkt kodu Unicode za pomocą sekwencji jednego lub dwóch 16-bitowych liczb całkowitych. Najbardziej typowe znaków Unicode wymagają tylko jeden punkt kodu UTF-16, mimo że dodatkowych znaków Unicode (U + 10000 lub nowszym) wymagają dwa punkty kodowe zastępczy UTF-16. Obsługiwane są zarówno zamówienia bajtów little-endian i big-endian.|Środowisko uruchomieniowe języka wspólnego kodowanie UTF-16 jest używana do reprezentowania <xref:System.Char> i <xref:System.String> wartości która jest używana przez system operacyjny Windows do reprezentowania `WCHAR` wartości.|  
|UTF-32|<xref:System.Text.UTF32Encoding>|Reprezentuje każdy punkt kodu Unicode jako liczba całkowita 32-bitowych. Obsługiwane są zarówno zamówienia bajtów little-endian i big-endian.|Kodowanie UTF-32 jest używany, jeśli chcesz uniknąć zachowanie punktu kodu zastępczy kodowanie UTF-16 w systemach operacyjnych, dla których zakodowany miejsca jest zbyt ważne aplikacje. Nadal można zakodować pojedynczego symbole renderowany na ekranie za pomocą więcej niż jednego znaku UTF-32.|  
|Kodowania ANSI/ISO||Zapewnia obsługę różnych stron kodowych. W systemach operacyjnych Windows stron kodowych są używane do obsługi określonego języka lub grupę języków. Dla tabeli, która zawiera listę stron kodowych obsługiwanych przez .NET, zobacz <xref:System.Text.Encoding> klasy. Możesz pobrać obiekt kodowania dla strony kodu określonego przez wywołanie metody <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> metody.|Strona kodowa zawiera 256 punkty kodowe i jest liczony od zera. W większości stron kodowych punkty kodowe od 0 do 127 reprezentuje zestaw znaków ASCII, a punkty kodowe 128 do 255 różni się znacznie między stron kodowych. Na przykład strona kodowa 1252 przewiduje znaków łaciński pisania systemy, w tym angielski, niemiecki i francuski. Ostatnie punkty kodowe 128 w na stronie kodowej 1252 zawierają znaki akcentu. Strona kodowa 1253 zawiera kody znaków, które są wymagane w systemie greckim zapisu. Ostatnie punkty kodowe 128 w na stronie kodowej 1253 zawierać znaków greckich. W rezultacie aplikację, która opiera się na stronach kodowych ANSI nie można zapisać grecki i niemieckim w tym samym strumieniu tekstu, chyba że zawiera on identyfikator, który wskazuje stronę kodu.|  
|Zestaw znaków dwubajtowych kodowania (znaków znaków DBCS)||Obsługa języków, takich jak chiński i japoński, koreański, które zawierają więcej niż 256 znaków. W zestawie DBCS parę punkty kodowe (dwubajtowe) reprezentuje każdy znak. <xref:System.Text.Encoding.IsSingleByte%2A?displayProperty=nameWithType> Właściwość zwraca `false` dla kodowań znaków Dwubajtowych. Możesz pobrać obiekt kodowania dla określonego znaków Dwubajtowych, wywołując <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> metody.|W zestawie DBCS parę punkty kodowe (dwubajtowe) reprezentuje każdy znak. Jeśli aplikacja obsługuje dane DBCS, pierwszego bajtu znaków DBCS (bajt) są przetwarzane w połączeniu z bajt, który następuje bezpośrednio po jej. Ponieważ jedna para punkty kodowe dwubajtowe mogą reprezentować różne znaki, w zależności od strony kodowej, ten schemat nadal nie zezwala na kombinację dwóch języków, takich jak japońskim i chińskim, w tym samym strumieniu danych.|  
  
 Tych kodowaniach umożliwiają pracę ze znakami Unicode, a także przy użyciu kodowania, które są najczęściej używane w przypadku starszych aplikacji. Ponadto można utworzyć niestandardowego kodowania, definiując klasę, która pochodzi od klasy <xref:System.Text.Encoding> i przesłanianie jej członków.  
  
### <a name="platform-notes-includenetcoreincludesnet-core-mdmd"></a>Uwagi dotyczące platformy: [!INCLUDE[net_core](../../../includes/net-core-md.md)]  
 Domyślnie [!INCLUDE[net_core](../../../includes/net-core-md.md)] nie udostępnia żadnych stron kodowych innych niż strona kodowa 28591 i kodowania Unicode, takich jak UTF-8 i UTF-16. Można jednak dodać stron kodowych w standardowe aplikacje Windows znaleziono obiektu docelowego .NET do aplikacji. Aby uzyskać pełne informacje, zobacz <xref:System.Text.CodePagesEncodingProvider> tematu.  
  
<a name="Selecting"></a>   
## <a name="selecting-an-encoding-class"></a>Wybieranie klasy kodowania  
 Jeśli masz możliwość wyboru kodowanie do użycia przez aplikację, należy użyć kodowania Unicode najlepiej albo <xref:System.Text.UTF8Encoding> lub <xref:System.Text.UnicodeEncoding>. (.NET obsługuje również trzeci kodowanie Unicode, <xref:System.Text.UTF32Encoding>.)  
  
 Jeśli planowane jest używane kodowanie ASCII (<xref:System.Text.ASCIIEncoding>), wybierz <xref:System.Text.UTF8Encoding> zamiast tego. Dwa kodowania są identyczne dla zestawu znaków ASCII, ale <xref:System.Text.UTF8Encoding> ma następujące zalety:  
  
-   Może ona reprezentować każdego znaku Unicode, natomiast <xref:System.Text.ASCIIEncoding> obsługuje tylko znak Unicode wartości od U + 0000 i U + 007F.  
  
-   Zapewnia ona wykrywanie błędów i większe bezpieczeństwo.  
  
-   On ma zostać dostosowana do można tak szybko, jak to możliwe i powinien być szybciej niż inne kodowanie. Nawet w przypadku zawartości, która jest całkowicie ASCII, operacje wykonywane przy użyciu <xref:System.Text.UTF8Encoding> są szybsze niż operacje wykonywane przy użyciu <xref:System.Text.ASCIIEncoding>.  
  
 Należy rozważyć użycie <xref:System.Text.ASCIIEncoding> tylko w przypadku starszych aplikacji. Jednak nawet w przypadku starszych aplikacji <xref:System.Text.UTF8Encoding> może być lepszym rozwiązaniem w następujących sytuacjach (zakładając, że ustawienia domyślne):  
  
-   Jeśli aplikacja ma zawartość, która nie jest ściśle ASCII i koduje go jako <xref:System.Text.ASCIIEncoding>, każdy znak spoza zestawu ASCII kodowane jako znak zapytania (?). Jeśli następnie aplikacja dekoduje tych danych, informacje zostaną utracone.  
  
-   Jeśli aplikacja ma zawartość, która nie jest ściśle ASCII i koduje go jako <xref:System.Text.UTF8Encoding>, wynik jest niezrozumiały, jeśli jest interpretowany jako ASCII. Jednak jeśli następnie aplikacja używa dekodera UTF-8 do zdekodowania tych danych, dane wykonuje pomyślnie komunikacji dwustronnej.  
  
 W aplikacji sieci web powinny odzwierciedlać znaków wysłane do klienta w odpowiedzi na żądania sieci web, kodowanie, używany przez klienta. W większości przypadków należy ustawić <xref:System.Web.HttpResponse.ContentEncoding%2A?displayProperty=nameWithType> właściwości do wartości zwracanej przez <xref:System.Web.HttpRequest.ContentEncoding%2A?displayProperty=nameWithType> właściwości do wyświetlania tekstu w kodowaniu, że użytkownik oczekuje.  
  
<a name="Using"></a>   
## <a name="using-an-encoding-object"></a>Używanie obiektu kodowania  
 Koder konwertuje ciąg znaków (najczęściej znakami Unicode) na jej liczbowy (bajtów) równoważne. Koder ASCII może na przykład użyć, aby skonwertować znaki Unicode ASCII, tak, aby można było je wyświetlić w konsoli. Aby dokonać konwersji, należy wywołać <xref:System.Text.Encoding.GetBytes%2A?displayProperty=nameWithType> metody. Jeśli chcesz określić liczbę bajtów są niezbędne do przechowywania zakodowanych znaków przed wykonaniem, kodowanie, można wywołać <xref:System.Text.Encoding.GetByteCount%2A> metody.  
  
 W poniższym przykładzie użyto tablicy jednobajtowych do zakodowania ciągów w dwie oddzielne operacje. Obsługuje ona indeks wskazującą położenie początkowe w tablicy bajtowej dla następnego zestawu bajtów zakodowane w formacie ASCII. Wywołuje <xref:System.Text.ASCIIEncoding.GetByteCount%28System.String%29?displayProperty=nameWithType> metodę, aby upewnić się, że tablica bajtów jest wystarczająco duża, aby pomieścić ciąg zakodowany. Następnie wywołuje <xref:System.Text.ASCIIEncoding.GetBytes%28System.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Byte%5B%5D%2CSystem.Int32%29?displayProperty=nameWithType> metody do kodowania znaków w ciągu.  
  
 [!code-csharp[Conceptual.Encoding#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/getbytes1.cs#8)]
 [!code-vb[Conceptual.Encoding#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/getbytes1.vb#8)]  
  
 Dekoder konwertuje tablica bajtów, która odzwierciedla kodowania określony znak do zestawu znaków w tablicy znaków lub w ciągu. Aby zdekodować tablicy bajtów w tablicy znaków, należy wywołać <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> metody. Aby zdekodować tablicy bajtów na ciąg znaków, należy wywołać <xref:System.Text.Encoding.GetString%2A> metody. Jeśli chcesz określić, ile znaków są niezbędne do przechowywania zdekodowany bajtów przed wykonaniem dekodowanie, można wywołać <xref:System.Text.Encoding.GetCharCount%2A> metody.  
  
 Poniższy przykład trzy ciągi koduje i dekoduje je do jednej tablicy znaków. Obsługuje ona indeks wskazującą położenie początkowe w tablicy znaków dla następnego zestawu znaków zdekodowanego. Wywołuje <xref:System.Text.ASCIIEncoding.GetCharCount%2A> metody, aby upewnić się, że tablicy znaków jest wystarczająco duża, aby pomieścić wszystkich znaków zdekodowanego. Następnie wywołuje <xref:System.Text.ASCIIEncoding.GetChars%28System.Byte%5B%5D%2CSystem.Int32%2CSystem.Int32%2CSystem.Char%5B%5D%2CSystem.Int32%29?displayProperty=nameWithType> metoda zdekodować tablicy bajtów.  
  
 [!code-csharp[Conceptual.Encoding#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/getchars1.cs#9)]
 [!code-vb[Conceptual.Encoding#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/getchars1.vb#9)]  
  
 Kodowanie i dekodowanie metody klasy pochodne <xref:System.Text.Encoding> zostały zaprojektowane do pracy w kompletny zestaw danych; oznacza to, że wszystkie dane, aby być szyfrowanym lub dekodowanym jest dostarczany w pojedynczym wywołaniu metody. Jednak w niektórych przypadkach dane są dostępne w strumieniu, a dane można szyfrowanym lub dekodowanym może znajdować się tylko z oddzielnych operacji odczytu. Wymaga to operację kodowania lub dekodowania do zapamiętania dowolny zapisany stan z jego poprzedniego wywołania. Metody klas pochodnych <xref:System.Text.Encoder> i <xref:System.Text.Decoder> są w stanie obsłużyć kodowania i dekodowania operacje obejmujące wiele wywołań metody.  
  
 <xref:System.Text.Encoder> Obiekt określonego kodowania jest dostępny w tym kodowania firmy <xref:System.Text.Encoding.GetEncoder%2A?displayProperty=nameWithType> właściwości. A <xref:System.Text.Decoder> obiekt określonego kodowania jest dostępny w tym kodowania firmy <xref:System.Text.Encoding.GetDecoder%2A?displayProperty=nameWithType> właściwości. Dekodowania operacji, należy pamiętać, że klasy pochodne klasy <xref:System.Text.Decoder> obejmują <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> metody, ale nie ma metody, która odnosi się do <xref:System.Text.Encoding.GetString%2A?displayProperty=nameWithType>.  
  
 Poniższy przykład ilustruje różnicę między <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> i <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> metody dekodowania tablicy bajtów Unicode. Przykład koduje ciąg, który zawiera niektóre znaki Unicode w pliku, a następnie używa dwie metody dekodowania zdekodować instrukcje na temat dziesięć bajtów w danym momencie. Ponieważ para zastępcza odbywa się w bajtach dziesiątego i jedenasty, są dekodowane w wywołaniach oddzielnych metodach. Dane wyjściowe pokazują, <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> metoda nie jest w stanie prawidłowo zdekodować bajtów i zamiast tego zastępuje je U + FFFD (znak zastępczy). Z drugiej strony <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> metoda jest w stanie pomyślnie zdekodować tablicy bajtów, aby uzyskać oryginalny ciąg.  
  
 [!code-csharp[Conceptual.Encoding#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/stream1.cs#10)]
 [!code-vb[Conceptual.Encoding#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/stream1.vb#10)]  
  
<a name="FallbackStrategy"></a>   
## <a name="choosing-a-fallback-strategy"></a>Wybieranie strategii rezerwowe  
 Gdy metoda podejmuje próbę kodowania i dekodowania znak, ale nie istnieje żadne mapowanie, musi on implementować strategia rezerwowa, który określa sposób obsługi mapowania nie powiodło się. Istnieją trzy typy rezerwowego strategii:  
  
-   Rezerwowe najlepszego dopasowania  
  
-   Zastąpienie rezerwowe  
  
-   Wyjątek rezerwowe  
  
> [!IMPORTANT]
>  Najbardziej typowe problemy podczas operacji kodowania wystąpić, gdy znak Unicode nie można zamapować na kodowanie strony określonego kodu. Najbardziej typowe problemy w dekodowanie operacje wystąpić, gdy sekwencje nieprawidłowy bajt nie można przetłumaczyć prawidłowych znaków Unicode. Z tego względu należy wiedzieć rezerwowego strategię, jakiej używa określonego obiektu kodowania. Jeśli to możliwe, należy określić strategia rezerwowa używane przez obiekt kodowania, podczas tworzenia wystąpienia obiektu.  
  
<a name="BestFit"></a>   
### <a name="best-fit-fallback"></a>Rezerwowe najlepszego dopasowania  
 Jeśli znak nie ma dokładnego dopasowania w kodowanie docelowe, kodera może podjąć próbę zamapowania go na podobny znak. (Rezerwowe najlepszego dopasowania jest przede wszystkim kodowania zamiast dekodowania problem. Istnieje bardzo niewiele stron kodowych, które zawierają znaki nie mogą być poprawnie mapowane na Unicode.) Rezerwowe najlepszego dopasowania jest ustawieniem domyślnym dla strony kodowej i kodowania, które są pobierane przez zestaw znaków dwubajtowych <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> i <xref:System.Text.Encoding.GetEncoding%28System.String%29?displayProperty=nameWithType> przeciążenia.  
  
> [!NOTE]
>  Teoretycznie kodowania Unicode klasy w .NET (<xref:System.Text.UTF8Encoding>, <xref:System.Text.UnicodeEncoding>, i <xref:System.Text.UTF32Encoding>) obsługę każdego znaku w każdym zestawie znaków, dzięki czemu może służyć, aby wyeliminować najlepszego dopasowania rezerwowego problemów.  
  
 Strategie najlepszego dopasowania się różnić w przypadku różne strony kodowe. Na przykład dla niektórych stron kodowych łaciński pełnej szerokości znaków mapy w celu bardziej powszechne połowę szerokości znaków alfabetu łacińskiego. To mapowanie nie jest tworzona dla innych stron kodowych. Nawet w skuteczną strategię najlepszego dopasowania nie ma żadnych imaginable nadające się do niektórych znaków w niektórych kodowania. Na przykład chińskich ideogramów nie ma uzasadnione mapowania na stronę kodową 1252. W tym przypadku jest używany ciąg zastępujący. Domyślnie ten ciąg jest tylko pojedynczy znak zapytania (U + 003F).  
  
> [!NOTE]
>  Strategie najlepszego dopasowania nie opisano szczegółowo. Jednak kilka stron kodowych są udokumentowane na [konsorcjum Unicode](https://www.unicode.org/Public/MAPPINGS/VENDORS/MICSFT/WindowsBestFit/) witryny sieci Web. Przejrzyj **readme.txt** plików w tym folderze opis jak interpretować pliki mapowania.
  
 W poniższym przykładzie użyto strony kodowej 1252 (Windows stronę kodową dla języków zachodnich Europejskiego), aby zilustrować mapowanie najlepszego dopasowania i jej wady. <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> Metoda służy do pobierania obiektu kodowania dla strony kodowej 1252. Domyślnie używa dla znaków Unicode, których nie obsługuje mapowanie najlepszego dopasowania. Przykład tworzy ciąg, który zawiera trzy znaki spoza ASCII - KÓŁKACH LATIN CAPITAL LETTER S (U + 24C 8), DROBNY PIĘĆ (U + 2075), a INFINITY (U + 221E) - rozdzielone spacjami. Wynika z przykładu pokazują, gdy ten ciąg jest zakodowany w trzech oryginalne znaki inne niż miejsca są zastępowane przez znak zapytania (U + 003F), PIĘCIU CYFR (U + 0035) i osiem CYFR (U + 0038). OSIEM CYFR zastępuje szczególnie niską nieobsługiwany znak NIESKOŃCZONOŚCI i znak zapytania oznacza, że żadne mapowanie była dostępna dla oryginalnego znaku.  
  
 [!code-csharp[Conceptual.Encoding#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1.cs#1)]
 [!code-vb[Conceptual.Encoding#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1.vb#1)]  
  
 Mapowanie jest domyślnym zachowaniem <xref:System.Text.Encoding> obiektu kodującej danych Unicode do danych strony kodowej, a istnieją starsze aplikacje, które zależą od tego zachowania. Jednak większość nowych aplikacji należy unikać najlepszego dopasowania zachowanie ze względów bezpieczeństwa. Na przykład aplikacje powinny nie umieszczać nazwy domeny za pomocą kodowania najlepszego dopasowania.  
  
> [!NOTE]
>  Możesz również wdrożyć niestandardowe mapowanie rezerwowego najlepszego dopasowania dla kodowania. Aby uzyskać więcej informacji, zobacz [realizację strategii rezerwowe niestandardowe](../../../docs/standard/base-types/character-encoding.md#Custom) sekcji.  
  
 Jeśli rezerwowe najlepszego dopasowania jest ustawieniem domyślnym dla obiektu kodowania, możesz wybrać inny strategia rezerwowa po pobraniu <xref:System.Text.Encoding> obiektu przez wywołanie metody <xref:System.Text.Encoding.GetEncoding%28System.Int32%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> lub <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> przeciążenia. Poniższa sekcja zawiera przykład, który zastępuje każdy znak, który nie może być mapowana na stronę kodową 1252 gwiazdką (*).  
  
 [!code-csharp[Conceptual.Encoding#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1a.cs#3)]
 [!code-vb[Conceptual.Encoding#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1a.vb#3)]  
  
<a name="Replacement"></a>   
### <a name="replacement-fallback"></a>Zastąpienie rezerwowe  
 Jeśli znak nie ma dokładnego dopasowania w systemie docelowym, ale istnieje nie odpowiednie znak, który mogą być mapowane na, aplikacja może określić znak zastępczy lub ciąg. Jest to domyślne zachowanie dla dekoder Unicode, która zastępuje dowolnej sekwencji dwubajtowy, który nie można go zdekodować REPLACEMENT_CHARACTER (U + FFFD). Warto również domyślne zachowanie <xref:System.Text.ASCIIEncoding> klasy, która zastępuje każdy znak, który go nie kodowania i dekodowania znakiem zapytania. Poniższy przykład ilustruje znaków zastępczych dla ciągu Unicode z poprzedniego przykładu. Dane wyjściowe pokazują, każdy znak, który można odkodować wartości bajtów ASCII zastępuje 0x3F, co w kodzie ASCII, znaku zapytania.  
  
 [!code-csharp[Conceptual.Encoding#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/replacementascii.cs#2)]
 [!code-vb[Conceptual.Encoding#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/replacementascii.vb#2)]  
  
 .NET zawiera <xref:System.Text.EncoderReplacementFallback> i <xref:System.Text.DecoderReplacementFallback> klasy, które Zastąp ciąg zastępujący, jeśli znak nie jest mapowany w kodowania lub dekodowania operacji. Domyślnie ten ciąg zastępczy jest znak zapytania, ale można wywoływać przeciążenia konstruktora klasy, aby wybrać inny ciąg. Zazwyczaj w ciągu zamiennym jest pojedynczy znak, ale nie jest wymagane. Poniższy przykład umożliwia zmianę zachowania kodera strona 1252 kodu przez utworzenie wystąpienia <xref:System.Text.EncoderReplacementFallback> obiektu, który używa znak gwiazdki (*) jako ciąg zastępujący.  
  
 [!code-csharp[Conceptual.Encoding#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1a.cs#3)]
 [!code-vb[Conceptual.Encoding#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1a.vb#3)]  
  
> [!NOTE]
>  Możesz również wdrożyć zastępczej klasie dla kodowania. Aby uzyskać więcej informacji, zobacz [realizację strategii rezerwowe niestandardowe](../../../docs/standard/base-types/character-encoding.md#Custom) sekcji.  
  
 Oprócz znaku zapytania (U + 003F) znak zastępczy Unicode (U + FFFD) jest często stosowany jako ciąg zastępujący, szczególnie w przypadku, gdy dekodowanie sekwencje bajtów, które nie można pomyślnie przekształcić znaków Unicode. Jednak masz swobodę wyboru każdy ciąg zastępczy i może zawierać wiele znaków.  
  
<a name="Exception"></a>   
### <a name="exception-fallback"></a>Wyjątek rezerwowe  
 Zamiast podawać najlepszego dopasowania rezerwowe lub ciąg zastępujący, może zgłosić koder <xref:System.Text.EncoderFallbackException> Jeśli nie może zakodować zestawu znaków i może zgłosić dekodera <xref:System.Text.DecoderFallbackException> przypadku nie można zdekodować tablicy bajtów. Aby zgłosić wyjątek w kodowania i dekodowania operacje, podaj <xref:System.Text.EncoderExceptionFallback> obiektu i <xref:System.Text.DecoderExceptionFallback> obiektu, odpowiednio do <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> metody. Poniższy przykład ilustruje wyjątków rezerwowego z <xref:System.Text.ASCIIEncoding> klasy.  
  
 [!code-csharp[Conceptual.Encoding#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/exceptionascii.cs#4)]
 [!code-vb[Conceptual.Encoding#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/exceptionascii.vb#4)]  
  
> [!NOTE]
>  Można również zaimplementować niestandardowy wyjątek procedury obsługi dla operacji kodowania. Aby uzyskać więcej informacji, zobacz [realizację strategii rezerwowe niestandardowe](../../../docs/standard/base-types/character-encoding.md#Custom) sekcji.  
  
 <xref:System.Text.EncoderFallbackException> i <xref:System.Text.DecoderFallbackException> obiektów należy podać następujące informacje o warunku, który spowodował wyjątek:  
  
-   <xref:System.Text.EncoderFallbackException> Obiekt zawiera <xref:System.Text.EncoderFallbackException.IsUnknownSurrogate%2A> metody, która wskazuje, czy znak lub znaki, które nie może zostać zakodowana reprezentują para zastępcza Nieznany (w tym przypadku metoda ta zwraca `true`) lub nieznany pojedynczego znaku (w takiej sytuacji, metoda zwraca `false`). Znaki w para zastępcza są dostępne z <xref:System.Text.EncoderFallbackException.CharUnknownHigh%2A?displayProperty=nameWithType> i <xref:System.Text.EncoderFallbackException.CharUnknownLow%2A?displayProperty=nameWithType> właściwości. Nieznany pojedynczy znak jest dostępne z <xref:System.Text.EncoderFallbackException.CharUnknown%2A?displayProperty=nameWithType> właściwości. <xref:System.Text.EncoderFallbackException.Index%2A?displayProperty=nameWithType> Właściwość wskazuje pozycji w ciągu odnaleziono pierwszy znak, który nie jest zaszyfrowana.  
  
-   <xref:System.Text.DecoderFallbackException> Obiekt zawiera <xref:System.Text.DecoderFallbackException.BytesUnknown%2A> właściwość, która zwraca tablicę bajtów, które nie mogą zostać zdekodowane. <xref:System.Text.DecoderFallbackException.Index%2A?displayProperty=nameWithType> Właściwość wskazuje pozycję początkową nieznany bajtów.  
  
 Mimo że <xref:System.Text.EncoderFallbackException> i <xref:System.Text.DecoderFallbackException> obiektów podaj odpowiednie informacje diagnostyczne o wyjątku, nie zapewniają one dostęp do kodowania lub dekodowania buforu. W związku z tym nie zezwalają na nieprawidłowe dane do zastąpienia lub poprawione w metodzie kodowania lub dekodowania.  
  
<a name="Custom"></a>   
## <a name="implementing-a-custom-fallback-strategy"></a>Implementowanie niestandardowego strategia rezerwowa  
 Oprócz mapowanie najlepszego dopasowania są implementowane wewnętrznie przez stron kodowych, .NET zawiera następujące klasy do implementowania strategia rezerwowa:  
  
-   Użyj <xref:System.Text.EncoderReplacementFallback> i <xref:System.Text.EncoderReplacementFallbackBuffer> zostać zastąpione znaki kodowania operacji.  
  
-   Użyj <xref:System.Text.DecoderReplacementFallback> i <xref:System.Text.DecoderReplacementFallbackBuffer> do zastąpienia znaków dekodowanie operacji.  
  
-   Użyj <xref:System.Text.EncoderExceptionFallback> i <xref:System.Text.EncoderExceptionFallbackBuffer> zgłosić <xref:System.Text.EncoderFallbackException> po znaku nie może być zakodowany.  
  
-   Użyj <xref:System.Text.DecoderExceptionFallback> i <xref:System.Text.DecoderExceptionFallbackBuffer> zgłosić <xref:System.Text.DecoderFallbackException> po znaku nie mogą zostać zdekodowane.  
  
 Ponadto można zaimplementować niestandardowego rozwiązania, które używa rezerwowe najlepszego dopasowania, rezerwowy zastąpienia lub rezerwowe wyjątek, wykonaj następujące czynności:  
  
1. Wyprowadzić klasę z <xref:System.Text.EncoderFallback> operacji kodowania i z <xref:System.Text.DecoderFallback> dekodowania operacji.  
  
2. Wyprowadzić klasę z <xref:System.Text.EncoderFallbackBuffer> operacji kodowania i z <xref:System.Text.DecoderFallbackBuffer> dekodowania operacji.  
  
3. Do rezerwowej, gdy wyjątek jest wstępnie zdefiniowane <xref:System.Text.EncoderFallbackException> i <xref:System.Text.DecoderFallbackException> klasy nie spełnia Twoich potrzeb, takich jak wyprowadzenia klasy z obiektu wyjątku <xref:System.Exception> lub <xref:System.ArgumentException>.  
  
### <a name="deriving-from-encoderfallback-or-decoderfallback"></a>Wyprowadzanie z EncoderFallback lub DecoderFallback  
 Aby zaimplementować niestandardowe rozwiązanie alternatywne, należy utworzyć klasę, która dziedziczy po elemencie <xref:System.Text.EncoderFallback> operacji kodowania i z <xref:System.Text.DecoderFallback> dekodowania operacji. Wystąpień tych klas są przekazywane do <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> metod i jako pośrednik między klasą kodowania i implementacji rezerwowej.  
  
 Podczas tworzenia niestandardowego rozwiązania rezerwowe dla koder i dekoder, należy zaimplementować następujące elementy członkowskie:  
  
-   <xref:System.Text.EncoderFallback.MaxCharCount%2A?displayProperty=nameWithType> Lub <xref:System.Text.DecoderFallback.MaxCharCount%2A?displayProperty=nameWithType> właściwość, która zwraca maksymalną liczbę znaków, które mogą rezerwowego najlepszego dopasowania, wymiana albo wyjątek wróć do Zamień jeden znak. Dla niestandardowego wyjątku rezerwowy jego wartość wynosi zero.  
  
-   <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> Lub <xref:System.Text.DecoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> metody, która zwraca niestandardowe <xref:System.Text.EncoderFallbackBuffer> lub <xref:System.Text.DecoderFallbackBuffer> implementacji. Metoda jest wywoływana przez koder po napotkaniu pierwszego znaku, który nie może pomyślnie kodowanie lub przez dekoder, po napotkaniu pierwszego bajtu, która nie może pomyślnie dekodowania.  
  
### <a name="deriving-from-encoderfallbackbuffer-or-decoderfallbackbuffer"></a>Wyprowadzanie z EncoderFallbackBuffer lub DecoderFallbackBuffer  
 Aby zaimplementować niestandardowe rozwiązanie alternatywne, również należy utworzyć klasę, która dziedziczy po elemencie <xref:System.Text.EncoderFallbackBuffer> operacji kodowania i z <xref:System.Text.DecoderFallbackBuffer> dekodowania operacji. Wystąpień tych klas są zwracane przez <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A> metody <xref:System.Text.EncoderFallback> i <xref:System.Text.DecoderFallback> klasy. <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> Metoda jest wywoływana przez koder po napotkaniu pierwszego znaku, który nie jest możliwe do kodowania, i <xref:System.Text.DecoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> metoda jest wywoływana przez dekoder po napotkaniu co najmniej jeden bajtów, które nie jest w stanie do odkodowania. <xref:System.Text.EncoderFallbackBuffer> i <xref:System.Text.DecoderFallbackBuffer> klasy zapewniają implementacji rezerwowej. Każde wystąpienie reprezentuje bufor, który zawiera znaki powrotu, które zastąpi znak, który nie może zostać zakodowana lub sekwencja bajtów, które nie mogą zostać zdekodowane.  
  
 Podczas tworzenia niestandardowego rozwiązania rezerwowe dla koder i dekoder, należy zaimplementować następujące elementy członkowskie:  
  
-   <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> Lub <xref:System.Text.DecoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> metody. <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> jest wywoływana przez koder zapewnienie bufora rezerwowy z informacjami o znak, który go nie można zakodować. Ponieważ znak, który ma być zdekodowany, może być para zastępcza, ta metoda jest przeciążony. Kilkoma przeciążeniami jest przekazywany znak, który ma być zdekodowany i jej indeks w ciągu. Drugie przeciążenie jest przekazywany wysokim i niskim zastępcze wraz z jej indeks w ciągu. <xref:System.Text.DecoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> Metoda jest wywoływana przez dekoder zapewnienie bufora rezerwowy informacji na temat bajtów, które nie można go zdekodować. Ta metoda jest przekazywana tablicę bajtów, które nie można go zdekodować, wraz z indeks pierwszego bajtu. Określ metodę planu awaryjnego powinna zwrócić `true` Jeśli bufora rezerwowy może dostarczyć najlepszego dopasowania lub znak zastępczy lub znaków dwubajtowych; w przeciwnym razie powinna zwrócić `false`. Dla wyjątku rezerwowy Określ metodę planu awaryjnego należy zgłosić wyjątek.  
  
-   <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> Lub <xref:System.Text.DecoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> metody, która jest wywoływana wielokrotnie przez koder lub dekoder, które można pobrać następny znak z bufora rezerwowy. Gdy wszystkie znaki powrotu zostały zwrócone, metoda powinna zwrócić U + 0000.  
  
-   <xref:System.Text.EncoderFallbackBuffer.Remaining%2A?displayProperty=nameWithType> Lub <xref:System.Text.DecoderFallbackBuffer.Remaining%2A?displayProperty=nameWithType> właściwość, która zwraca liczbę pozostałych znaków w buforze rezerwowego.  
  
-   <xref:System.Text.EncoderFallbackBuffer.MovePrevious%2A?displayProperty=nameWithType> Lub <xref:System.Text.DecoderFallbackBuffer.MovePrevious%2A?displayProperty=nameWithType> metody, która przenosi bieżąca pozycja w buforze rezerwowym poprzedni znak.  
  
-   <xref:System.Text.EncoderFallbackBuffer.Reset%2A?displayProperty=nameWithType> Lub <xref:System.Text.DecoderFallbackBuffer.Reset%2A?displayProperty=nameWithType> metody, która ponownie inicjuje bufora rezerwowy.  
  
 W przypadku powrotu najlepszego dopasowania lub zastąpienie rezerwowe implementacji rezerwowej klasy pochodne klasy <xref:System.Text.EncoderFallbackBuffer> i <xref:System.Text.DecoderFallbackBuffer> również utrzymania dwa pola wystąpieniem prywatnym: Dokładna liczba znaków w buforze; i indeks następnego znaku bufor do zwrócenia.  
  
### <a name="an-encoderfallback-example"></a>Przykład EncoderFallback  
 Wcześniejszy przykład używany zastąpienie rezerwowego do zastępowania znaków Unicode, który nie odpowiada na znaki ASCII gwiazdką (*). W poniższym przykładzie użyto niestandardowych implementacji rezerwowej najlepszego dopasowania zamiast tego, aby zapewnić lepsze mapowanie znaki spoza zestawu ASCII.  
  
 Poniższy kod definiuje klasę o nazwie `CustomMapper` , jest tworzony na podstawie <xref:System.Text.EncoderFallback> do obsługi mapowanie najlepszego dopasowania znaki spoza zestawu ASCII. Jego `CreateFallbackBuffer` metoda zwraca `CustomMapperFallbackBuffer` obiektu, który zapewnia <xref:System.Text.EncoderFallbackBuffer> implementacji. `CustomMapper` Klasy używa <xref:System.Collections.Generic.Dictionary%602> obiekt ma być przechowywany mapowania nieobsługiwane znaki Unicode (wartość klucza) i ich odpowiadające im znaki 8-bitową, (które są przechowywane w dwóch następujących po sobie bajtów w 64-bitowa liczba całkowita). Aby udostępnić to mapowanie bufora rezerwowy, `CustomMapper` wystąpienia jest przekazywany jako parametr do `CustomMapperFallbackBuffer` konstruktora klasy. Ponieważ najdłuższy mapowanie jest ciąg "INF" znak Unicode, U + 221E, `MaxCharCount` właściwość zwraca wartość 3.  
  
 [!code-csharp[Conceptual.Encoding#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#5)]
 [!code-vb[Conceptual.Encoding#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#5)]  
  
 Poniższy kod definiuje `CustomMapperFallbackBuffer` klasy, która jest pochodną <xref:System.Text.EncoderFallbackBuffer>. Słownik zawierający mapowanie najlepszego dopasowania i który jest zdefiniowany w `CustomMapper` wystąpienie jest dostępne z jej konstruktora klasy. Jego `Fallback` metoda zwraca `true` ewentualne znaków Unicode, których nie można zakodować kodera ASCII są zdefiniowane w słowniku mapowania; w przeciwnym razie zwraca `false`. Dla każdego działania rezerwowego prywatna `count` zmienna oznacza liczbę znaków, które będą jeszcze zwracane i prywatna `index` zmiennej wskazuje pozycję buforu ciągu `charsToReturn`, następnego znaku do zwrócenia.  
  
 [!code-csharp[Conceptual.Encoding#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#6)]
 [!code-vb[Conceptual.Encoding#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#6)]  
  
 Poniższy kod tworzy następnie wystąpienie `CustomMapper` obiektu i przekazuje go do wystąpienia <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> metody. Dane wyjściowe wskazują, że najlepszego dopasowania implementacji rezerwowej pomyślnie obsługuje trzy znaki spoza zestawu ASCII w oryginalnym ciągu.  
  
 [!code-csharp[Conceptual.Encoding#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#7)]
 [!code-vb[Conceptual.Encoding#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#7)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Text.Encoder>
- <xref:System.Text.Decoder>
- <xref:System.Text.DecoderFallback>
- <xref:System.Text.Encoding>
- <xref:System.Text.EncoderFallback>
- [Lokalizacja i globalizacja](../../../docs/standard/globalization-localization/index.md)
