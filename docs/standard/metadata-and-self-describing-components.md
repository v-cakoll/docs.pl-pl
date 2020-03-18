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
ms.openlocfilehash: a4f4c0e1af379d31c5b478472780d5c7de813bf6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121932"
---
# <a name="metadata-and-self-describing-components"></a>Składniki samoopisujące się i metadane

W przeszłości składnik oprogramowania (exe lub .dll), który został napisany w jednym języku, nie mógł łatwo użyć składnika oprogramowania napisanego w innym języku. COM stanowił krok w kierunku rozwiązania tego problemu. .NET Framework sprawia, że współdziałanie składników jeszcze łatwiejsze, umożliwiając kompilatory emitować dodatkowe informacje deklaratywne do wszystkich modułów i zestawów. Te informacje, zwane metadanymi, pomagają składnikom bezproblemowo współdziałać.

 Metadane to informacje binarne opisujące program, który jest przechowywany w pliku przenośnego pliku wykonywalnego w czasie wykonywania języka wspólnego języka lub w pamięci. Podczas kompilowania kodu do pliku PE metadane są wstawiane do jednej części pliku, a kod jest konwertowany na język pośredni firmy Microsoft (MSIL) i wstawiany do innej części pliku. Każdy typ i element członkowski, który jest zdefiniowany i odwołuje się w module lub zestawie jest opisany w metadanych. Gdy kod jest wykonywany, czas wykonywania ładuje metadane do pamięci i odwołuje się do niego, aby odnajdować informacje o klasach kodu, członków, dziedziczenia i tak dalej.

 Metadane opisuje każdy typ i element członkowski zdefiniowane w kodzie w sposób neutralny dla języka. W metadanych przechowywane są następujące informacje:

- Opis złożenia.

  - Tożsamość (nazwa, wersja, kultura, klucz publiczny).

  - Typy, które są eksportowane.

  - Inne zestawy, od których zależy ten zestaw.

  - Uprawnienia zabezpieczeń potrzebne do uruchomienia.

- Opis typów.

  - Zaimplementowano nazwę, widoczność, klasę podstawową i interfejsy.

  - Elementy członkowskie (metody, pola, właściwości, zdarzenia, typy zagnieżdżone).

- Atrybuty.

  - Dodatkowe elementy opisowe, które modyfikują typy i elementy członkowskie.

## <a name="benefits-of-metadata"></a>Zalety metadanych

Metadane są kluczem do prostszego modelu programowania i eliminują potrzebę plików języka definicji interfejsu (IDL), plików nagłówkowych lub jakiejkolwiek zewnętrznej metody odwołania się do składnika. Metadane umożliwia językom .NET Framework automatyczne opisywanie się w sposób neutralny pod względem języka, niewidoczny zarówno przez dewelopera, jak i użytkownika. Ponadto metadane można rozszerzyć za pomocą atrybutów. Metadane zapewniają następujące główne korzyści:

- Pliki samoopisujące się.

  Wspólne moduły wykonywania języka i zestawy są samoopisujące. Metadane modułu zawierają wszystko, co jest potrzebne do interakcji z innym modułem. Metadane automatycznie udostępnia funkcje IDL w modelu COM, dzięki czemu można użyć jednego pliku zarówno do definicji i implementacji. Moduły i zestawy czasu wykonywania nie wymagają nawet rejestracji w systemie operacyjnym. W rezultacie opisy używane przez program runtime zawsze odzwierciedlają rzeczywisty kod w skompilowanym pliku, co zwiększa niezawodność aplikacji.

- Interoperacyjność językowa i łatwiejszy projekt oparty na komponentach.

  Metadane zawiera wszystkie informacje wymagane o skompilowany kod, aby odziedziczyć klasę z pliku PE napisane w innym języku. Można utworzyć wystąpienie dowolnej klasy napisane w dowolnym języku zarządzanym (dowolny język, który jest przeznaczony dla języka uruchomieniowego języka wspólnego) bez martwienia się o jawne organizowanie lub przy użyciu niestandardowego kodu współdziałania.

- Atrybuty.

  Program .NET Framework umożliwia deklarowanie określonych rodzajów metadanych, nazywanych atrybutami, w skompilowanym pliku. Atrybuty można znaleźć w całej platformy .NET Framework i są używane do kontrolowania bardziej szczegółowo, jak program zachowuje się w czasie wykonywania. Ponadto można emitować własne niestandardowe metadane do plików .NET Framework za pomocą atrybutów niestandardowych zdefiniowanych przez użytkownika. Aby uzyskać więcej informacji, zobacz [Atrybuty](../../docs/standard/attributes/index.md).

## <a name="metadata-and-the-pe-file-structure"></a>Struktura pliku PE i metadanych

Metadane są przechowywane w jednej sekcji przenośnego pliku wykonywalnego (PE) środowiska .NET Framework, podczas gdy kod w języku Microsoft Intermediate Language (MSIL) jest przechowywany w innej sekcji pliku PE. Część pliku stanowiąca metadane zawiera szereg struktur danych w postaci tabeli i stosu. Część MSIL zawiera kod języka MSIL i tokeny metadanych, które odwołują się do części pliku PE stanowiącej metadane. Tokeny metadanych mogą wystąpić podczas korzystania z narzędzi, takich jak [Disassembler MSIL (Ildasm.exe)](../../docs/framework/tools/ildasm-exe-il-disassembler.md) do wyświetlania kodu MSIL, na przykład.

### <a name="metadata-tables-and-heaps"></a>Tabele i stosy metadanych

Każda tabela metadanych zawiera informacje o elementach programu. Na przykład jedna tabela metadanych opisuje klasy w kodzie, inna opisuje pola itd. Jeśli w kodzie istnieje dziesięć klas, tabela klas będzie zawierała dziesięć wierszy, po jednym dla każdej klasy. Tabele metadanych odwołują się do innych tabel i stosów. Na przykład tabela metadanych klas odwołuje się do tabeli metod.

W metadanych informacje są przechowywane w czterech strukturach stosów: ciągu tekstowym, dużym obiekcie binarnym, ciągu tekstowym użytkownika i identyfikatorze GUID. Wszystkie ciągi tekstowe używane do nazywania typów i elementów członkowskich są przechowywane w stosie będącym ciągiem tekstowym. Na przykład tabela metod nie przechowuje bezpośrednio nazwy konkretnej metody, ale wskazuje nazwę metody zapisaną w stercie będącej ciągiem tekstowym.

### <a name="metadata-tokens"></a>Tokeny metadanych

Każdy wiersz w każdej tabeli metadanych jest jednoznacznie identyfikowany w części MSIL pliku PE za pomocą tokenu metadanych. Koncepcyjnie tokeny metadanych przypominają wskaźniki utrwalone w kodzie MSIL, które odwołują się do określonej tabeli metadanych.

Token metadanych jest czterobajtową liczbą. Pierwszy bajt określa tabelę metadanych, do której odwołuje się dany token (metoda, typ itd.). Pozostałe trzy bajty określają wiersz w tabeli metadanych, który odpowiada opisywanemu elementowi programistycznemu. Jeśli metoda zostanie zdefiniowana w języku C# i skompilowana do pliku PE, w części MSIL pliku PE może się pojawić poniższy token metadanych:

`0x06000004`

Górny bajt`0x06`( ) wskazuje, że jest to token **MethodDef.** Niższe trzy bajty`000004`( ) informuje program runtime języka wspólnego szukać w czwartym wierszu **MethodDef** tabeli informacji, które opisuje tę definicję metody.

### <a name="metadata-within-a-pe-file"></a>Metadane w pliku PE

Gdy program jest kompilowany dla środowiska uruchomieniowego języka wspólnego, ulega przekształceniu na plik PE składający się z trzech części. W tabeli poniżej opisano zawartość każdej części.

|Sekcja PE|Zawartość sekcji PE|
|----------------|----------------------------|
|Nagłówek PE|Indeks głównych sekcji pliku PE i adres punktu wejścia.<br /><br /> Na podstawie tych informacji środowisko uruchomieniowe identyfikuje plik jako plik PE i ustala podczas ładowania programu do pamięci, gdzie się rozpoczyna wykonywanie.|
|MSIL — Instrukcje|Instrukcje języka Microsoft Intermediate Language (MSIL) tworzące kod. Wielu instrukcjom MSIL towarzyszą tokeny metadanych.|
|Metadane|Tabele i stosy metadanych. Na podstawie tej sekcji środowisko uruchomieniowe rejestruje informacje o każdym typie i elemencie członkowskim istniejącym w kodzie. Ta sekcja zawiera również niestandardowe atrybuty i informacje o zabezpieczeniach.|

## <a name="run-time-use-of-metadata"></a>Użycie metadanych w czasie wykonywania

Aby lepiej zrozumieć metadane i jego rolę w czasie wykonywania języka wspólnego, może być pomocne skonstruować prosty program i zilustrować, jak metadane wpływa na jego okres użytkowania. Poniższy przykład kodu pokazuje dwie metody `MyApp`wewnątrz klasy o nazwie . Metoda `Main` jest punktem wejścia programu, `Add` podczas gdy metoda po prostu zwraca sumę dwóch argumentów całkowitych.

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

Po uruchomieniu kodu, czas wykonywania ładuje moduł do pamięci i konsultuje się z metadanymi dla tej klasy. Po załadowaniu program runtime przeprowadza obszerną analizę strumienia języka pośredniego (MSIL) metody, aby przekonwertować go na szybkie instrukcje komputera macierzystego. W czasie wykonywania używa kompilatora just-in-time (JIT) do konwertowania instrukcji MSIL do natywnego kodu maszynowego jednej metody w razie potrzeby.

W poniższym przykładzie przedstawiono część MSIL produkowane `Main` z funkcji poprzedniego kodu. MSIL i metadane można wyświetlić z dowolnej aplikacji .NET Framework przy użyciu [pliku MSIL Disassembler (Ildasm.exe).](../../docs/framework/tools/ildasm-exe-il-disassembler.md)

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

Kompilator JIT odczytuje MSIL dla całej metody, analizuje ją dokładnie i generuje wydajne instrukcje macierzyste dla metody. W `IL_000d`przypadku tokenu metadanych `Add` `/*` `06000003 */`dla metody ( ) jest napotkany i w czasie wykonywania używa tokenu, aby zapoznać się z trzecim wierszem **MethodDef** tabeli.

W poniższej tabeli przedstawiono część tabeli **MethodDef,** do której `Add` odwołuje się token metadanych opisujący metodę. Podczas gdy inne tabele metadanych istnieją w tym zestawie i mają własne unikatowe wartości, omówiono tylko tę tabelę.

|Wiersz|Względny adres wirtualny (RVA)|ImplFlags|Flagi|Nazwa<br /><br /> (Wskazuje stertę ciągu).|Podpis (wskazuje stertę obiektu blob).|
|---------|--------------------------------------|---------------|-----------|-----------------------------------------|----------------------------------------|
|1|0x00002050|IL<br /><br /> Zarządzani|Public<br /><br /> Ponowne użycieSlot<br /><br /> Specialname<br /><br /> Nazwa RTSpecialName<br /><br /> .ctor (ctor)|.ctor (konstruktor)||
|2|0x00002058|IL<br /><br /> Zarządzani|Public<br /><br /> Statyczny<br /><br /> Ponowne użycieSlot|Główne|Ciąg|
|3|0x0000208c|IL<br /><br /> Zarządzani|Public<br /><br /> Statyczny<br /><br /> Ponowne użycieSlot|Dodaj|int, int, int|

Każda kolumna tabeli zawiera ważne informacje o kodzie. Kolumna **RVA** umożliwia programowi runtime obliczenie początkowego adresu pamięci msil, który definiuje tę metodę. **ImplFlags** i **Flags** kolumny zawierają maski bitowe, które opisują metodę (na przykład, czy metoda jest publiczna lub prywatna). Kolumna **Nazwa** indeksuje nazwę metody ze sterty ciągu. Kolumna **Podpis** indeksuje definicję podpisu metody w stercie obiektu blob.

Czas wykonywania oblicza żądany adres przesunięcia z kolumny **RVA** w trzecim wierszu i zwraca ten adres do kompilatora JIT, który następnie przechodzi do nowego adresu. Kompilator JIT kontynuuje przetwarzanie MSIL pod nowym adresem, dopóki nie napotka innego tokenu metadanych, a proces zostanie powtórzony.

Przy użyciu metadanych, czas wykonywania ma dostęp do wszystkich informacji potrzebnych do załadowania kodu i przetworzyć go na macierzyste instrukcje komputera. W ten sposób metadane umożliwia samoopisujące się pliki i, wraz z systemem typowych typów, dziedziczenie w wielu językach.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Atrybuty](../../docs/standard/attributes/index.md)|W tym artykule opisano sposób stosowania atrybutów, pisania atrybutów niestandardowych i pobierania informacji przechowywanych w atrybutach.|
