---
title: Składniki samoopisujące się i metadane
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- runtime, metadata
- languages, interoperability
- portable executable files, metadata
- self-describing files
- metadata, about metadata
- common language runtime, metadata
- PE files, metadata
- components [.NET Framework], metadata
ms.assetid: 3dd13c5d-a508-455b-8dce-0a852882a5a7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a35f4ffa88211d914dbf84c87da49fafa89a929
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353897"
---
# <a name="metadata-and-self-describing-components"></a>Składniki samoopisujące się i metadane

W przeszłości składnik oprogramowania (. exe lub. dll), który został zapisany w jednym języku, nie mógł łatwo korzystać ze składnika oprogramowania, który został zapisany w innym języku. COM podano krok prowadzący do rozwiązania tego problemu. .NET Framework sprawia, że współdziałanie składników jest jeszcze łatwiejsze, dzięki czemu kompilatory mogą emitować dodatkowe informacje deklaracyjne do wszystkich modułów i zestawów. Te informacje, nazywane metadanymi, ułatwiają bezproblemowe współdziałanie ze składnikami.

 Metadane to informacje binarne opisujące program, który jest przechowywany w pliku wykonywalnym środowiska uruchomieniowego języka wspólnego (PE) lub w pamięci. Podczas kompilowania kodu do pliku PE metadane są wstawiane do jednej części pliku, a kod jest konwertowany do języka pośredniego firmy Microsoft (MSIL) i wstawiany do innej części pliku. Każdy typ i element członkowski, który jest zdefiniowany i przywoływany w module lub zestawie, jest opisany w metadanych. Gdy kod jest wykonywany, środowisko uruchomieniowe ładuje metadane do pamięci i odwołuje się do niego, aby odnaleźć informacje o klasach, elementach członkowskich, dziedziczeniu i tak dalej.

 Metadane opisują każdy typ i element członkowski zdefiniowane w kodzie w sposób niezależny od języka. Metadane przechowują następujące informacje:

- Opis zestawu.

  - Tożsamość (nazwa, wersja, kultura, klucz publiczny).

  - Typy, które są eksportowane.

  - Inne zestawy, od których zależy ten zestaw.

  - Uprawnienia zabezpieczeń, które są konieczne do uruchomienia programu.

- Opis typów.

  - Wdrożono nazwę, widoczność, klasę bazową i interfejsy.

  - Elementy członkowskie (metody, pola, właściwości, zdarzenia, typy zagnieżdżone).

- Attributes.

  - Dodatkowe opisowe elementy, które modyfikują typy i elementy członkowskie.

## <a name="benefits-of-metadata"></a>Zalety metadanych

Metadane to prostszy model programowania i eliminuje konieczność stosowania plików języka definicji interfejsu (IDL), plików nagłówkowe lub wszelkich zewnętrznych metod odwołania do składników. Metadane umożliwiają .NET Framework językach opisywania automatycznie w sposób niezależny od języka, niewidocznych dla deweloperów i użytkowników. Ponadto metadane są rozszerzalne przy użyciu atrybutów. Metadane zapewniają następujące korzyści:

- Pliki z własnymi opisami.

  Moduły i zestawy środowiska uruchomieniowego języka wspólnego są samodzielne. Metadane modułu zawierają wszystkie elementy potrzebne do współdziałania z innym modułem. Metadane automatycznie udostępniają funkcje IDL w modelu COM, dlatego można użyć jednego pliku dla definicji i implementacji. Moduły i zestawy środowiska uruchomieniowego nie wymagają rejestracji w systemie operacyjnym. W związku z tym opisy używane przez środowisko uruchomieniowe zawsze odzwierciedlają rzeczywisty kod w skompilowanym pliku, co zwiększa niezawodność aplikacji.

- Współdziałanie języków i łatwiejsza konstrukcja oparta na składnikach.

  Metadane zawierają wszystkie informacje wymagane na temat skompilowanego kodu, aby dziedziczyć klasę z pliku PE, który został zapisany w innym języku. Można utworzyć wystąpienie klasy, która jest zapisywana w dowolnym języku zarządzanym (dowolny język, który jest przeznaczony dla środowiska uruchomieniowego języka wspólnego) bez obaw o jawne kierowanie lub użycie niestandardowego kodu współdziałania.

- Attributes.

  .NET Framework umożliwia deklarowanie określonych rodzajów metadanych o nazwie Attributes w skompilowanym pliku. Atrybuty można znaleźć w części .NET Framework i służą do kontrolowania bardziej szczegółowych informacji o zachowaniu programu w czasie wykonywania. Ponadto można emitować własne metadane niestandardowe do plików .NET Framework za poorednictwem niestandardowych atrybutów zdefiniowanych przez użytkownika. Aby uzyskać więcej informacji, zobacz [atrybuty](../../docs/standard/attributes/index.md).

## <a name="metadata-and-the-pe-file-structure"></a>Struktura pliku PE i metadanych

Metadane są przechowywane w jednej sekcji przenośnego pliku wykonywalnego (PE) środowiska .NET Framework, podczas gdy kod w języku Microsoft Intermediate Language (MSIL) jest przechowywany w innej sekcji pliku PE. Część pliku stanowiąca metadane zawiera szereg struktur danych w postaci tabeli i stosu. Część MSIL zawiera kod języka MSIL i tokeny metadanych, które odwołują się do części pliku PE stanowiącej metadane. Tokeny metadanych mogą wystąpić podczas korzystania z narzędzi takich jak [Dezasembler MSIL (Ildasm. exe)](../../docs/framework/tools/ildasm-exe-il-disassembler.md) w celu wyświetlenia na przykład kodu MSIL.

### <a name="metadata-tables-and-heaps"></a>Tabele i stosy metadanych

Każda tabela metadanych zawiera informacje o elementach programu. Na przykład jedna tabela metadanych opisuje klasy w kodzie, inna opisuje pola itd. Jeśli w kodzie istnieje dziesięć klas, tabela klas będzie zawierała dziesięć wierszy, po jednym dla każdej klasy. Tabele metadanych odwołują się do innych tabel i stosów. Na przykład tabela metadanych klas odwołuje się do tabeli metod.

W metadanych informacje są przechowywane w czterech strukturach stosów: ciągu tekstowym, dużym obiekcie binarnym, ciągu tekstowym użytkownika i identyfikatorze GUID. Wszystkie ciągi tekstowe używane do nazywania typów i elementów członkowskich są przechowywane w stosie będącym ciągiem tekstowym. Na przykład tabela metod nie przechowuje bezpośrednio nazwy konkretnej metody, ale wskazuje nazwę metody zapisaną w stercie będącej ciągiem tekstowym.

### <a name="metadata-tokens"></a>Tokeny metadanych

Każdy wiersz w każdej tabeli metadanych jest jednoznacznie identyfikowany w części MSIL pliku PE za pomocą tokenu metadanych. Koncepcyjnie tokeny metadanych przypominają wskaźniki utrwalone w kodzie MSIL, które odwołują się do określonej tabeli metadanych.

Token metadanych jest czterobajtową liczbą. Pierwszy bajt określa tabelę metadanych, do której odwołuje się dany token (metoda, typ itd.). Pozostałe trzy bajty określają wiersz w tabeli metadanych, który odpowiada opisywanemu elementowi programistycznemu. Jeśli metoda zostanie zdefiniowana w języku C# i skompilowana do pliku PE, w części MSIL pliku PE może się pojawić poniższy token metadanych:

`0x06000004`

Górny bajt (`0x06`) wskazuje, że jest to token **MethodDef** . Trzy mniejsze bajty (`000004`) mówią, że środowisko uruchomieniowe języka wspólnego zapoznaje się z czwartym wierszem tabeli **MethodDef** , aby uzyskać informacje opisujące tę definicję metody.

### <a name="metadata-within-a-pe-file"></a>Metadane w pliku PE

Gdy program jest kompilowany dla środowiska uruchomieniowego języka wspólnego, ulega przekształceniu na plik PE składający się z trzech części. W tabeli poniżej opisano zawartość każdej części.

|Sekcja PE|Zawartość sekcji PE|
|----------------|----------------------------|
|Nagłówek PE|Indeks głównych sekcji pliku PE i adres punktu wejścia.<br /><br /> Na podstawie tych informacji środowisko uruchomieniowe identyfikuje plik jako plik PE i ustala podczas ładowania programu do pamięci, gdzie się rozpoczyna wykonywanie.|
|MSIL — Instrukcje|Instrukcje języka Microsoft Intermediate Language (MSIL) tworzące kod. Wielu instrukcjom MSIL towarzyszą tokeny metadanych.|
|Metadane|Tabele i stosy metadanych. Na podstawie tej sekcji środowisko uruchomieniowe rejestruje informacje o każdym typie i elemencie członkowskim istniejącym w kodzie. Ta sekcja zawiera również niestandardowe atrybuty i informacje o zabezpieczeniach.|

## <a name="run-time-use-of-metadata"></a>Użycie metadanych w czasie wykonywania

Aby lepiej zrozumieć metadane i jego rolę w środowisku uruchomieniowym języka wspólnego, może być przydatne utworzenie prostego programu i zilustrowanie, jak metadane wpływają na jego żywotność. Poniższy przykład kodu przedstawia dwie metody wewnątrz klasy o nazwie `MyApp`. Metoda `Main` jest punktem wejścia programu, a metoda `Add` po prostu zwraca sumę dwóch argumentów liczb całkowitych.

```vb
Public Class MyApp
   Public Shared Sub Main()
      Dim ValueOne As Integer = 10
      Dim ValueTwo As Integer = 20
      Console.WriteLine("The Value is: {0}", Add(ValueOne, ValueTwo))
   End Sub

   Public Shared Function Add(One As Integer, Two As Integer) As Integer
      Return (One + Two)
   End Function
End Class
```

```csharp
using System;
public class MyApp
{
   public static int Main()
   {
      int ValueOne = 10;
      int ValueTwo = 20;
      Console.WriteLine("The Value is: {0}", Add(ValueOne, ValueTwo));
      return 0;
   }
   public static int Add(int One, int Two)
   {
      return (One + Two);
   }
}
```

Po uruchomieniu kodu środowisko uruchomieniowe ładuje moduł do pamięci i sprawdza metadane tej klasy. Po załadowaniu środowisko uruchomieniowe wykonuje szeroką analizę strumienia języka pośredniego (MSIL) metody firmy Microsoft w celu przeprowadzenia konwersji na szybkie instrukcje maszyn natywnych. Środowisko uruchomieniowe używa kompilatora just-in-Time (JIT) do konwertowania instrukcji MSIL na natywny kod maszynowy po jednej metodzie w razie potrzeby.

W poniższym przykładzie przedstawiono część MSIL wygenerowanego na podstawie poprzedniego kodu funkcja `Main`. Można wyświetlić MSIL i metadane z dowolnych aplikacji .NET Framework przy użyciu [Dezasembler MSIL (Ildasm. exe)](../../docs/framework/tools/ildasm-exe-il-disassembler.md).

```console
.entrypoint
.maxstack  3
.locals ([0] int32 ValueOne,
         [1] int32 ValueTwo,
         [2] int32 V_2,
         [3] int32 V_3)
IL_0000:  ldc.i4.s   10
IL_0002:  stloc.0
IL_0003:  ldc.i4.s   20
IL_0005:  stloc.1
IL_0006:  ldstr      "The Value is: {0}"
IL_000b:  ldloc.0
IL_000c:  ldloc.1
IL_000d:  call int32 ConsoleApplication.MyApp::Add(int32,int32) /* 06000003 */
```

Kompilator JIT odczytuje MSIL dla całej metody, analizuje ją dokładnie i generuje wydajne instrukcje natywne dla metody. W `IL_000d` występuje token metadanych dla metody `Add` (`/*` `06000003 */`), a środowisko uruchomieniowe użyje tokenu do zapoznania się z trzecim wierszem tabeli **MethodDef** .

W poniższej tabeli przedstawiono część tabeli **MethodDef** , do której odwołuje się token metadanych opisującą metodę `Add`. Chociaż inne tabele metadanych istnieją w tym zestawie i mają własne unikatowe wartości, omawiana jest tylko ta tabela.

|Wiersz|Względny adres wirtualny (RVA)|ImplFlags|flagi|Name<br /><br /> (Punkty do sterty ciągu).|Podpis (punkty do sterty obiektów BLOB).|
|---------|--------------------------------------|---------------|-----------|-----------------------------------------|----------------------------------------|
|1|0x00002050|IL<br /><br /> Zarządzanych|Public<br /><br /> ReuseSlot<br /><br /> Jako SpecialName<br /><br /> RTSpecialName<br /><br /> . ctor|. ctor (Konstruktor)||
|2|0x00002058|IL<br /><br /> Zarządzanych|Public<br /><br /> Static<br /><br /> ReuseSlot|główną|String|
|3|0x0000208c|IL<br /><br /> Zarządzanych|Public<br /><br /> Static<br /><br /> ReuseSlot|Add|int, int, int|

Każda kolumna tabeli zawiera ważne informacje o kodzie. Kolumna **RVA** umożliwia środowisko uruchomieniowe Obliczanie adresu pamięci początkowej, który definiuje tę metodę. Kolumny **ImplFlags** i **flag** zawierają masek bitowych opisujące metodę (na przykład czy metoda jest publiczna lub prywatna). Kolumna **name** indeksuje nazwę metody z sterty ciągu. Kolumna **Signature** indeksuje definicję sygnatury metody w stercie obiektów BLOB.

Środowisko uruchomieniowe oblicza żądany adres przesunięcia z kolumny **RVA** w trzecim wierszu i zwraca ten adres do kompilatora JIT, który następnie przechodzi do nowego adresu. Kompilator JIT kontynuuje przetwarzanie MSIL pod nowym adresem do momentu napotkania innego tokenu metadanych, a proces jest powtarzany.

Przy użyciu metadanych środowisko uruchomieniowe ma dostęp do wszystkich informacji potrzebnych do załadowania kodu i przetworzyć je w natywnych instrukcjach dotyczących maszyn. W ten sposób metadane umożliwiają samodzielne opisywanie plików oraz, wraz ze wspólnym systemem typów, dziedziczenie między językami.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Atrybuty](../../docs/standard/attributes/index.md)|Opisuje sposób stosowania atrybutów, pisania atrybutów niestandardowych i pobierania informacji przechowywanych w atrybutach.|
