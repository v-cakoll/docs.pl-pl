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
ms.openlocfilehash: 8ccfb0dee0eb6380d48498ba61f763eb777bded1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754948"
---
# <a name="metadata-and-self-describing-components"></a>Składniki samoopisujące się i metadane

W przeszłości składnik oprogramowania (.exe lub .dll), który został napisany w jednym języku nie można łatwo użyć składnika oprogramowania, który został zapisany w innym języku. COM, pod warunkiem krok w rozwiązaniu tego problemu. .NET Framework ułatwia współdziałanie składników nawet, umożliwiając kompilatory do emitowania dodatkowe informacje deklaratywne na wszystkich modułach i zestawach. Te informacje o nazwie metadane, pomaga składniki bezproblemowo wchodzić w interakcje.

 Metadane są binarne informacje opisujące programu, który jest przechowywany w pliku przenośny plik wykonywalny (PE) środowiska uruchomieniowego języka wspólnego lub w pamięci. Podczas kompilowania kodu do pliku PE, metadane są wstawiane do jednej części pliku, a kod jest konwertowany na składnię języka Microsoft intermediate language (MSIL) i wstawione do innej części pliku. Każdy typów i elementów członkowskich, który został zdefiniowany i jest przywoływany w module, zestaw jest opisany w metadanych. Gdy kod jest wykonywany, środowisko uruchomieniowe ładuje metadanych do pamięci i odwołuje się do niej, aby znaleźć informacje o klasy swój kod, elementy członkowskie, dziedziczenie i tak dalej.

 Metadane opisują co typów i elementów członkowskich, zdefiniowane w kodzie w sposób niezależny od języka. Metadane są przechowywane następujące informacje:

- Opis zestawu.

  - Tożsamość (nazwę, wersję, kulturę, klucz publiczny).

  - Typy, które są eksportowane.

  - Inne zestawy, od których zależy ten zestaw.

  - Uprawnienia zabezpieczeń wymagane do uruchomienia.

- Opis typów.

  - Nazwa, widoczność, klasa bazowa i interfejsy implementowane.

  - Członkowie (metody, pola, właściwości, zdarzenia, typów zagnieżdżonych).

- Atrybuty.

  - Dodatkowe elementy opisową, umożliwiające modyfikowanie typów i elementów członkowskich.

## <a name="benefits-of-metadata"></a>Korzyści z metadanych

Metadane ma kluczowe znaczenie prostszy model programowania i eliminuje potrzebę stosowania pliki języka definicji interfejsu (IDL), pliki nagłówkowe lub jakiejkolwiek jego metody zewnętrznej odwołanie do składnika. Metadane umożliwia językach środowiska .NET Framework do opisania się automatycznie w sposób niezależny od języka, niewidzianych zarówno przez dewelopera i użytkownika. Ponadto metadanych jest rozszerzalny za pomocą atrybutów. Metadane zawiera następujące główne zalety:

- Pliki samoopisujące.

  Samoopisujący są wspólnego moduły środowiska uruchomieniowego języka i zestawów. Metadane modułu zawiera wszystkie elementy potrzebne do interakcji z innego modułu. Metadane automatycznie zapewnia funkcje IDL w modelu COM, aby można było używać jeden plik, aby uzyskać definicję i implementację. Moduły środowiska uruchomieniowego i zestawów nawet nie wymagają rejestracji w systemie operacyjnym. W rezultacie nazw używanych przez środowisko uruchomieniowe zawsze odzwierciedlać rzeczywisty kod w pliku skompilowane, co zwiększa niezawodność aplikacji.

- Współdziałanie języków i łatwiejsze projekt oparty na komponentach.

  Metadane zawiera wszystkie wymagane informacje dotyczące skompilowany kod dla Ciebie dziedziczyć klasy z pliku PE zapisany w innym języku. Można utworzyć wystąpienia klasy napisane w dowolnym języku zarządzanych (dowolnego języka, który jest przeznaczony dla środowiska uruchomieniowego języka wspólnego) bez martwienia się o jawne kierowanie lub za pomocą kodu niestandardowego współdziałania.

- Atrybuty.

  .NET Framework pozwala zadeklarować konkretnych rodzajów metadanych o nazwie atrybutów, w pliku skompilowany. Atrybuty można znaleźć w całym programie .NET Framework i są używane do kontrolowania bardziej szczegółowo, w jaki program zachowuje się w czasie wykonywania. Ponadto może emitować metadane niestandardowe w plikach .NET Framework za pomocą atrybutów niestandardowych zdefiniowanych przez użytkownika. Aby uzyskać więcej informacji, zobacz [atrybuty](../../docs/standard/attributes/index.md).

## <a name="metadata-and-the-pe-file-structure"></a>Struktura pliku PE i metadanych

Metadane są przechowywane w jednej sekcji przenośnego pliku wykonywalnego (PE) środowiska .NET Framework, podczas gdy kod w języku Microsoft Intermediate Language (MSIL) jest przechowywany w innej sekcji pliku PE. Część pliku stanowiąca metadane zawiera szereg struktur danych w postaci tabeli i stosu. Część MSIL zawiera kod języka MSIL i tokeny metadanych, które odwołują się do części pliku PE stanowiącej metadane. Tokeny metadanych mogą występować w przypadku użyj narzędzi takich jak [MSIL Disassembler (Ildasm.exe)](../../docs/framework/tools/ildasm-exe-il-disassembler.md) Aby przeglądać kod zachowania MSIL, na przykład.

### <a name="metadata-tables-and-heaps"></a>Tabele i stosy metadanych

Każda tabela metadanych zawiera informacje o elementach programu. Na przykład jedna tabela metadanych opisuje klasy w kodzie, inna opisuje pola itd. Jeśli w kodzie istnieje dziesięć klas, tabela klas będzie zawierała dziesięć wierszy, po jednym dla każdej klasy. Tabele metadanych odwołują się do innych tabel i stosów. Na przykład tabela metadanych klas odwołuje się do tabeli metod.

W metadanych informacje są przechowywane w czterech strukturach stosów: ciągu tekstowym, dużym obiekcie binarnym, ciągu tekstowym użytkownika i identyfikatorze GUID. Wszystkie ciągi tekstowe używane do nazywania typów i elementów członkowskich są przechowywane w stosie będącym ciągiem tekstowym. Na przykład tabela metod nie przechowuje bezpośrednio nazwy konkretnej metody, ale wskazuje nazwę metody zapisaną w stercie będącej ciągiem tekstowym.

### <a name="metadata-tokens"></a>Tokeny metadanych

Każdy wiersz w każdej tabeli metadanych jest jednoznacznie identyfikowany w części MSIL pliku PE za pomocą tokenu metadanych. Koncepcyjnie tokeny metadanych przypominają wskaźniki utrwalone w kodzie MSIL, które odwołują się do określonej tabeli metadanych.

Token metadanych jest czterobajtową liczbą. Pierwszy bajt określa tabelę metadanych, do której odwołuje się dany token (metoda, typ itd.). Pozostałe trzy bajty określają wiersz w tabeli metadanych, który odpowiada opisywanemu elementowi programistycznemu. Jeśli metoda zostanie zdefiniowana w języku C# i skompilowana do pliku PE, w części MSIL pliku PE może się pojawić poniższy token metadanych:

```
0x06000004
```

Pierwszy bajt (`0x06`) wskazuje, że jest to **MethodDef** tokenu. Trzy bajty (`000004`) informuje środowisko uruchomieniowe języka wspólnego szukać w czwartym wierszu **MethodDef** tabeli że informacji opisujących tę definicję metody.

### <a name="metadata-within-a-pe-file"></a>Metadane w pliku PE

Gdy program jest kompilowany dla środowiska uruchomieniowego języka wspólnego, ulega przekształceniu na plik PE składający się z trzech części. W tabeli poniżej opisano zawartość każdej części.

|Sekcja PE|Zawartość sekcji PE|
|----------------|----------------------------|
|Nagłówek PE|Indeks głównych sekcji pliku PE i adres punktu wejścia.<br /><br /> Na podstawie tych informacji środowisko uruchomieniowe identyfikuje plik jako plik PE i ustala podczas ładowania programu do pamięci, gdzie się rozpoczyna wykonywanie.|
|MSIL — Instrukcje|Instrukcje języka Microsoft Intermediate Language (MSIL) tworzące kod. Wielu instrukcjom MSIL towarzyszą tokeny metadanych.|
|Metadane|Tabele i stosy metadanych. Na podstawie tej sekcji środowisko uruchomieniowe rejestruje informacje o każdym typie i elemencie członkowskim istniejącym w kodzie. Ta sekcja zawiera również niestandardowe atrybuty i informacje o zabezpieczeniach.|

## <a name="run-time-use-of-metadata"></a>Użycie metadanych w czasie wykonywania

Aby lepiej zrozumieć metadanych i jego rolę w środowisko uruchomieniowe języka wspólnego, może być przydatne do konstruowania prosty program i pokazują, jak metadane wpływa na jego życia czasu wykonywania. W poniższym przykładzie kodu pokazano dwie metody wewnątrz klasy o nazwie `MyApp`. `Main` Metodą jest punkt wejścia programu, gdy `Add` metoda po prostu zwraca sumę dwóch argumentów liczby całkowitej.

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

Gdy kod działa, środowisko uruchomieniowe ładuje moduł do pamięci i konsultacje dotyczące metadanych dla tej klasy. Po załadowaniu środowisko uruchomieniowe wykonuje rozbudowaną analizę metody Microsoft intermediate language (MSIL) stream, aby przekonwertować go do instrukcji maszyny macierzystej szybko. Środowisko wykonawcze używa kompilator just-in-time (JIT) do konwersji instrukcji MSIL do macierzystego kodu maszynowego jednej metody w danym momencie, zgodnie z potrzebami.

W poniższym przykładzie przedstawiono część MSIL wyprodukowanych z poprzednim kodzie `Main` funkcji. Można wyświetlić MSIL i metadanych z dowolnej platformy .NET Framework aplikacji za pomocą [MSIL Disassembler (Ildasm.exe)](../../docs/framework/tools/ildasm-exe-il-disassembler.md).

```
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

Kompilator JIT odczytuje MSIL dla całej metody, analizuje je dokładnie i generuje wydajne natywne instrukcje dla metody. W `IL_000d`, token metadanych dla `Add` — metoda (`/*` `06000003 */`) zostanie osiągnięty i środowisko wykonawcze używa tokenu zapoznać się z trzeciego wiersza **MethodDef** tabeli.

W poniższej tabeli przedstawiono część **MethodDef** tabeli przywoływanej przez token metadanych, który opisuje `Add` metody. Inne tabele metadanych istnieje w tym zestawie i mają własne unikatowe wartości, tylko w tej tabeli omówiono.

|Wiersz|Względnych adresów wirtualnych (RVA)|ImplFlags|Flagi|Nazwa<br /><br /> (Punkty na stercie będącej ciągiem tekstowym.)|Podpis (wskazuje sterty usługi blob).|
|---------|--------------------------------------|---------------|-----------|-----------------------------------------|----------------------------------------|
|1|0x00002050|IL<br /><br /> Zarządzane|Public<br /><br /> ReuseSlot<br /><br /> SpecialName<br /><br /> RTSpecialName<br /><br /> elementu .ctor|.ctor (Konstruktor)||
|2|0x00002058|IL<br /><br /> Zarządzane|Public<br /><br /> Static<br /><br /> ReuseSlot|Main|String|
|3|0x0000208c|IL<br /><br /> Zarządzane|Public<br /><br /> Static<br /><br /> ReuseSlot|Dodaj|int, int, int|

Każda kolumna tabeli zawiera ważne informacje o swoim kodzie. **RVA** kolumny pozwala środowiska uruchomieniowego obliczyć początkowy adres pamięci MSIL, który definiuje tę metodę. **Elementy ImplFlags** i **flagi** kolumny zawierają masek bitowych opisujące — metoda (na przykład, czy metoda jest publicznej lub prywatnej). **Nazwa** kolumny indeksuje nazwę metody w stercie będącej ciągiem tekstowym. **Podpisu** kolumny indeksuje definicja sygnatury metody w stosie obiektu blob.

Środowisko uruchomieniowe oblicza żądany adres przesunięcia od **RVA** kolumny w trzecim rzędzie i zwraca ten adres do kompilatora JIT, w której następnie przechodzi do nowego adresu. Kompilator JIT w dalszym ciągu przetwarzać MSIL na nowy adres, aż do napotkania inny token metadanych i proces jest powtarzany.

Przy użyciu metadanych, środowisko uruchomieniowe ma dostęp do wszystkich informacji, które musi załadować swój kod i przetworzyć te dane do instrukcji maszyny macierzystej. W ten sposób umożliwia metadanych pliki samoopisujące, a wraz z wspólny system typów, dziedziczenie między językami.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Atrybuty](../../docs/standard/attributes/index.md)|W tym artykule opisano, jak zastosować atrybutów, Zapis atrybutów niestandardowych i pobieranie informacji przechowywanych w atrybutach.|
