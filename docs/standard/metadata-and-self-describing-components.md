---
title: "Składniki samoopisujące się i metadane"
ms.custom: 
ms.date: 03/30/2017
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
- runtime, metadata
- languages, interoperability
- portable executable files, metadata
- self-describing files
- metadata, about metadata
- common language runtime, metadata
- PE files, metadata
- components [.NET Framework], metadata
ms.assetid: 3dd13c5d-a508-455b-8dce-0a852882a5a7
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ac08dcf305e8cc0c1a3be3b8300ed9981e7d84d4
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="metadata-and-self-describing-components"></a>Składniki samoopisujące się i metadane
W przeszłości składnika oprogramowania (.exe lub .dll), który został zapisany w jednym języku nie można łatwo użyć składnika oprogramowania, który został zapisany w innym języku. COM podany krok w rozwiązaniu tego problemu. .NET Framework ułatwia współdziałanie składnika nawet zezwalając kompilatory do emituje dodatkowe informacje deklaratywne do wszystkie moduły i zestawy. Te informacje o nazwie metadanych, pomaga składniki bezproblemowo interakcję.  
  
 Metadane są binarne informacje opisujące program, który jest przechowywany w pliku przenośny plik wykonywalny (PE) środowiska uruchomieniowego języka wspólnego lub w pamięci. Podczas kompilowania kodu w pliku PE, metadane są wstawiane do jednej części pliku, a kodu jest konwertowane na język pośredni firmy Microsoft (MSIL) i dodaje je w innym pliku. Każdy typ i element członkowski, który jest zdefiniowany i do którego odwołuje się moduł lub zestaw jest opisany w metadanych. Podczas wykonywania kodu środowiska uruchomieniowego ładuje metadanych w pamięci i odwołuje się do informacji o swój kod klasy, elementy członkowskie, dziedziczenia i tak dalej.  
  
 Metadane opisano każdy typ i elementu członkowskiego zdefiniowane w kodzie w sposób niezależny od języka. Metadane są przechowywane następujące informacje:  
  
-   Opis zestawu.  
  
    -   Tożsamość (nazwa, wersji, kultury, klucz publiczny).  
  
    -   Typy, które zostaną wyeksportowane.  
  
    -   Inne zestawy, które zależy od tego zestawu.  
  
    -   Uprawnienia zabezpieczeń wymagane do uruchomienia.  
  
-   Opis typów.  
  
    -   Nazwa, widoczność klasy podstawowej i interfejsy implementowane.  
  
    -   Elementy członkowskie (metody, pola, właściwości, zdarzenia, typy zagnieżdżone).  
  
-   Atrybuty.  
  
    -   Dodatkowe elementy opisowy, które modyfikowania typów i członków.  
  
## <a name="benefits-of-metadata"></a>Korzyści wynikające z metadanych  
 Metadane ma kluczowe znaczenie dla prostszy model programowania i eliminuje potrzebę stosowania pliki języka definicji interfejsu (IDL), pliki nagłówkowe lub jakiejkolwiek jego metody zewnętrznej odwołania do składnika. Metadane umożliwia języków .NET Framework do opisywania się automatycznie w sposób niezależny od języka, niewidocznym przez projektanta i użytkownika. Ponadto metadanych jest rozszerzalny za pomocą atrybutów. Metadane zapewniają następujące główne zalety:  
  
-   Pliki samoopisujące.  
  
     Modułów środowiska uruchomieniowego języka wspólnego i zestawy są samoopisujące. Metadane modułu zawiera wszystko, co jest potrzebne do interakcji z innego modułu. Metadane udostępnia automatycznie funkcjonalność IDL w modelu COM, dzięki czemu można użyć jednego pliku definicji i implementacji. Środowisko uruchomieniowe moduły i zestawy nawet nie wymagają rejestracji w systemie operacyjnym. W związku z tym nazw używanych przez środowisko uruchomieniowe zawsze odzwierciedlają rzeczywisty kod w skompilowanego pliku, co zwiększa niezawodność aplikacji.  
  
-   Współdziałanie języków i łatwiejsze projektowania opartego na składnikach.  
  
     Metadane zawiera wszystkie wymagane informacje dotyczące skompilowanego kodu można dziedziczyć klasy z pliku PE zapisany w innym języku. Można utworzyć wystąpienia klasy napisane w dowolnym języku zarządzanych (dowolnego języka, którego celem jest środowisko uruchomieniowe języka wspólnego), nie martwiąc się o jawne kierowanie lub za pomocą kodu niestandardowego współdziałania.  
  
-   Atrybuty.  
  
     .NET Framework pozwala zadeklarować określonych rodzajów metadanych o nazwie atrybutów w skompilowanego pliku. Atrybuty można znaleźć w programie .NET Framework i są używane do kontrolowania bardziej szczegółowo zachowanie programu w czasie wykonywania. Ponadto można wyemitować własnych niestandardowych metadanych do plików platformy .NET Framework za pomocą atrybutów niestandardowych zdefiniowanych przez użytkownika. Aby uzyskać więcej informacji, zobacz [atrybutów](../../docs/standard/attributes/index.md).  
  
## <a name="metadata-and-the-pe-file-structure"></a>Struktura pliku PE i metadanych  
 Metadane są przechowywane w jednej sekcji przenośnego pliku wykonywalnego (PE) środowiska .NET Framework, podczas gdy kod w języku Microsoft Intermediate Language (MSIL) jest przechowywany w innej sekcji pliku PE. Część pliku stanowiąca metadane zawiera szereg struktur danych w postaci tabeli i stosu. Część MSIL zawiera kod języka MSIL i tokeny metadanych, które odwołują się do części pliku PE stanowiącej metadane. Mogą wystąpić tokenów metadanych, korzystając z narzędzi takich jak [dezasembler MSIL (Ildasm.exe)](../../docs/framework/tools/ildasm-exe-il-disassembler.md) do wyświetlenia kodu na MSIL, np.  
  
### <a name="metadata-tables-and-heaps"></a>Tabele i stosy metadanych  
 Każda tabela metadanych zawiera informacje o elementach programu. Na przykład jedna tabela metadanych opisuje klasy w kodzie, inna opisuje pola itd. Jeśli w kodzie istnieje dziesięć klas, tabela klas będzie zawierała dziesięć wierszy, po jednym dla każdej klasy. Tabele metadanych odwołują się do innych tabel i stosów. Na przykład tabela metadanych klas odwołuje się do tabeli metod.  
  
 W metadanych informacje są przechowywane w czterech strukturach stosów: ciągu tekstowym, dużym obiekcie binarnym, ciągu tekstowym użytkownika i identyfikatorze GUID. Wszystkie ciągi tekstowe używane do nazywania typów i elementów członkowskich są przechowywane w stosie będącym ciągiem tekstowym. Na przykład tabela metod nie przechowuje bezpośrednio nazwy konkretnej metody, ale wskazuje nazwę metody zapisaną w stercie będącej ciągiem tekstowym.  
  
### <a name="metadata-tokens"></a>Tokeny metadanych  
 Każdy wiersz w każdej tabeli metadanych jest jednoznacznie identyfikowany w części MSIL pliku PE za pomocą tokenu metadanych. Koncepcyjnie tokeny metadanych przypominają wskaźniki utrwalone w kodzie MSIL, które odwołują się do określonej tabeli metadanych.  
  
 Token metadanych jest czterobajtową liczbą. Pierwszy bajt określa tabelę metadanych, do której odwołuje się dany token (metoda, typ itd.). Pozostałe trzy bajty określają wiersz w tabeli metadanych, który odpowiada opisywanemu elementowi programistycznemu. Jeśli metoda zostanie zdefiniowana w języku C# i skompilowana do pliku PE, w części MSIL pliku PE może się pojawić poniższy token metadanych:  
  
```  
0x06000004  
```  
  
 Górny bajtów (`0x06`) oznacza, że jest to **MethodDef** tokenu. Niższe trzy bajtów (`000004`) określa, że środowisko uruchomieniowe języka wspólnego do przeszukania czwartego wiersza **MethodDef** tabeli informacje opisujące to definicja metody.  
  
### <a name="metadata-within-a-pe-file"></a>Metadane w pliku PE  
 Gdy program jest kompilowany dla środowiska uruchomieniowego języka wspólnego, ulega przekształceniu na plik PE składający się z trzech części. W tabeli poniżej opisano zawartość każdej części.  
  
|Sekcja PE|Zawartość sekcji PE|  
|----------------|----------------------------|  
|Nagłówek PE|Indeks głównych sekcji pliku PE i adres punktu wejścia.<br /><br /> Na podstawie tych informacji środowisko uruchomieniowe identyfikuje plik jako plik PE i ustala podczas ładowania programu do pamięci, gdzie się rozpoczyna wykonywanie.|  
|MSIL — Instrukcje|Instrukcje języka Microsoft Intermediate Language (MSIL) tworzące kod. Wielu instrukcjom MSIL towarzyszą tokeny metadanych.|  
|Metadane|Tabele i stosy metadanych. Na podstawie tej sekcji środowisko uruchomieniowe rejestruje informacje o każdym typie i elemencie członkowskim istniejącym w kodzie. Ta sekcja zawiera również niestandardowe atrybuty i informacje o zabezpieczeniach.|  
  
## <a name="run-time-use-of-metadata"></a>Użycie metadanych w czasie wykonywania  
 Aby lepiej zrozumieć metadanych i swoją rolę w środowisku uruchomieniowym języka, może być przydatne do konstruowania prosty program i przedstawiają, jak metadanych ma wpływ na jego życia czasu wykonywania. W poniższym przykładzie kodu przedstawiono dwie metody w klasie o nazwie `MyApp`. `Main` Metody jest punkt wejścia programu, gdy `Add` metoda po prostu zwraca sumę dwóch argumentów liczby całkowitej.  
  
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
  
 Po uruchomieniu kodu środowiska uruchomieniowego ładuje moduł do pamięci i sprawdza metadanych dla tej klasy. Po załadowaniu środowiska uruchomieniowego wykonuje obszernej analizy strumienia język pośredni (MSIL) firmy Microsoft metody przekonwertować go do instrukcji fast natywny maszyny. Środowisko uruchomieniowe użyto kompilatora just in time (JIT) do przekonwertowania instrukcje MSIL kod natywny maszyny jednej metody w czasie, zgodnie z potrzebami.  
  
 W poniższym przykładzie przedstawiono część MSIL utworzone z poprzednim kodzie `Main` funkcji. Można wyświetlić MSIL i metadanych z dowolnej .NET Framework aplikacji za pomocą [dezasembler MSIL (Ildasm.exe)](../../docs/framework/tools/ildasm-exe-il-disassembler.md).  
  
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
  
 Kompilator JIT odczytuje MSIL dla całej metody, analizuje je dokładnie i generuje wydajne natywnego instrukcje dla metody. W `IL_000d`, token metadanych dla `Add` — metoda (`/*` `06000003 */`) napotkano środowiska uruchomieniowego tokenu i używa się trzeciego wiersza **MethodDef** tabeli.  
  
 W poniższej tabeli przedstawiono część **MethodDef** tabeli przywoływanej przez token metadanych, który opisuje `Add` metody. Inne tabele metadanych istnieje w tym zestawie i mają własne unikatowe wartości, tylko w tej tabeli omówiono.  
  
|Wiersz|Wirtualny adres względny (RVA)|Elementy ImplFlags|Flagi|Nazwa<br /><br /> (Wskazuje sterty ciągu).|Podpis (punkty sterty obiektu blob).|  
|---------|--------------------------------------|---------------|-----------|-----------------------------------------|----------------------------------------|  
|1|0x00002050|IL<br /><br /> Zarządzane|Public<br /><br /> ReuseSlot<br /><br /> Jako SpecialName<br /><br /> RTSpecialName<br /><br /> element .ctor|element .ctor (Konstruktor)||  
|2|0x00002058|IL<br /><br /> Zarządzane|Public<br /><br /> Static<br /><br /> ReuseSlot|Main|String|  
|3|0x0000208c|IL<br /><br /> Zarządzane|Public<br /><br /> Static<br /><br /> ReuseSlot|Dodaj|int, int, int|  
  
 Każda kolumna tabeli zawiera ważne informacje o kodzie. **Adres RVA** kolumna zezwala środowiska uruchomieniowego do obliczenia początkowy adres pamięci MSIL, który definiuje tę metodę. **Elementy ImplFlags** i **flagi** kolumny zawierają masek bitowych, który opisano metody (na przykład, czy metoda jest publicznym lub prywatnym). **Nazwa** kolumny indeksów nazwę metody sterty ciągu. **Podpisu** kolumny indeksów definicji podpis metody w sterty obiektu blob.  
  
 Środowisko uruchomieniowe oblicza żądany adres przesunięcia z **adres RVA** kolumny w trzecim wierszu i zwraca ten adres do kompilatora JIT, który następnie przechodzi do nowego adresu. Kompilator JIT w dalszym ciągu przetworzyć MSIL na nowy adres dopiero po napotkaniu inny token metadanych i proces jest powtarzany.  
  
 Przy użyciu metadanych, środowisko uruchomieniowe ma dostęp do wszystkich informacji wymaganych do kodu i przetwarza go do instrukcji natywny maszyny. W ten sposób umożliwia metadanych pliki samoopisujące i, wraz z wspólny system typów dziedziczenia wielu języków.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Atrybuty](../../docs/standard/attributes/index.md)|Opisuje sposób atrybutów, zapisywać atrybuty niestandardowe i pobieranie informacji przechowywanych w atrybutach.|
