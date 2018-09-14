---
title: Konwersja typów w programie .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- widening conversions
- explicit conversions
- narrowing conversions
- type conversion, about type conversion
- type conversion
- converting types
- narrowing coercion
- Explicit operator
- IConvertible interface
- base types, converting
- op_Implicit method
- widening coercion
- op_Explicit method
- Convert class
- implicit conversions
- Implicit operator
- data types [.NET Framework], converting
ms.assetid: ba36154f-064c-47d3-9f05-72f93a7ca96d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d039e591e1f61a7be18dc224845f82b107d918f
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45585840"
---
# <a name="type-conversion-in-the-net-framework"></a>Konwersja typów w programie .NET Framework
<a name="top"></a> Każda wartość ma skojarzony typ definiujący atrybuty, takie jak ilość miejsca przydzielonego dla wartości, zakres możliwych wartości, które może mieć i elementy członkowskie udostępniane. Wiele wartości można wyrazić za pomocą co najmniej dwóch typów. Na przykład wartość 4 może być wyrażona jako liczba całkowita lub wartość zmiennoprzecinkowa. Konwersja typu tworzy wartość nowego typu, która jest równoważna wartości starego typu, ale nie zawsze powoduje zachowanie tożsamości (dokładnej wartości) oryginalnego obiektu.  
  
 Program .NET Framework automatycznie obsługuje następujące konwersje:  
  
-   Konwersja z klasy pochodnej do klasy bazowej. Oznacza to, na przykład, że wystąpienia klasy lub struktury mogą być konwertowane na <xref:System.Object> wystąpienia.  Ta konwersja wymaga operatora rzutowania lub konwersji.  
  
-   Konwersja z klasy bazowej z powrotem do oryginalnej klasy pochodnej. W języku C# ta konwersja wymaga operatora rzutowania. W języku Visual Basic wymaga `CType` operator Jeśli `Option Strict` znajduje się na.  
  
-   Konwersja z typu, który implementuje interfejs do obiektu interfejsu, który reprezentuje ten interfejs. Ta konwersja wymaga operatora rzutowania lub konwersji.  
  
-   Konwersja obiektu interfejsu z powrotem do oryginalnego typu, który implementuje ten interfejs.  W języku C# ta konwersja wymaga operatora rzutowania. W języku Visual Basic wymaga `CType` operator Jeśli `Option Strict` znajduje się na.  
  
 Oprócz tych automatycznej konwersji [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] udostępnia kilka funkcji obsługujących konwersję typów niestandardowych. Należą do nich między innymi:  
  
-   `Implicit` Operatora, który definiuje dostępne rozszerzające konwersje między typami. Aby uzyskać więcej informacji, zobacz [niejawna konwersja za pomocą operatora Implicit](#implicit_conversion_with_the_implicit_operator) sekcji.  
  
-   `Explicit` Operatora, który definiuje dostępne zawężające konwersje między typami. Aby uzyskać więcej informacji, zobacz [jawna konwersja za pomocą operatora Explicit](#explicit_conversion_with_the_explicit_operator) sekcji.  
  
-   <xref:System.IConvertible> Interfejs, który definiuje konwersji do każdego z typów podstawowych danych .NET Framework. Aby uzyskać więcej informacji, zobacz [interfejs IConvertible](#the_iconvertible_interface) sekcji.  
  
-   <xref:System.Convert> Klasy, która udostępnia zestaw metod, które implementują metody w <xref:System.IConvertible> interfejsu. Aby uzyskać więcej informacji, zobacz [klasa Convert](#Convert) sekcji.  
  
-   <xref:System.ComponentModel.TypeConverter> Klasy, która jest klasą bazową, można rozszerzać w celu obsługi konwersji określonego typu do jakichkolwiek innych typów. Aby uzyskać więcej informacji, zobacz [klasa TypeConverter](#the_typeconverter_class) sekcji.  
  
<a name="implicit_conversion_with_the_implicit_operator"></a>   
## <a name="implicit-conversion-with-the-implicit-operator"></a>Niejawna konwersja za pomocą operatora Implicit  
 Konwersje rozszerzające obejmują utworzenie nowej wartości z wartości istniejącego typu, która ma bardziej ograniczony zakres lub bardziej ograniczoną listę elementów członkowskich niż typ docelowy. Konwersje rozszerzające nie mogą powodować utraty danych (chociaż mogą powodować utratę dokładności). Dane nie mogą być tracone, więc kompilatory mogą obsługiwać konwersję niejawnie (niewidocznie), dzięki czemu użytkownik nie musi używać jawnej metody konwersji ani operatora rzutowania.  
  
> [!NOTE]
>  Mimo że kod wywołujący niejawną konwersję może wywołać metodę konwersji lub użyć operatora rzutowania, ich użycie nie jest wymagane przez kompilatory obsługujące konwersje niejawne.  
  
 Na przykład <xref:System.Decimal> typ obsługuje niejawną konwersję z <xref:System.Byte>, <xref:System.Char>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.UInt16>, <xref:System.UInt32>, i <xref:System.UInt64> wartości. W poniższym przykładzie pokazano niektóre z tych niejawnych konwersji podczas przypisywania wartości do <xref:System.Decimal> zmiennej.  
  
 [!code-csharp[Conceptual.Conversion#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#1)]
 [!code-vb[Conceptual.Conversion#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#1)]  
  
 Jeśli kompilator określonego języka obsługuje operatory niestandardowe, niejawne konwersje można także definiować we własnych typach niestandardowych. W poniższym przykładzie pokazano częściową implementację typu danych bajtowych ze znakiem o nazwie `ByteWithSign` , który używa reprezentacji logowania i wielkości. Obsługuje niejawną konwersję z <xref:System.Byte> i <xref:System.SByte> wartości `ByteWithSign` wartości.  
  
 [!code-csharp[Conceptual.Conversion#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#2)]
 [!code-vb[Conceptual.Conversion#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#2)]  
  
 Następnie kod klienta może zadeklarować `ByteWithSign` zmiennej i przypisz mu <xref:System.Byte> i <xref:System.SByte> wartości bez wykonywania jawnych konwersji ani używania operatorów rzutowania, co ilustruje poniższy przykład.  
  
 [!code-csharp[Conceptual.Conversion#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#3)]
 [!code-vb[Conceptual.Conversion#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#3)]  
  
 [Powrót do początku](#top)  
  
<a name="explicit_conversion_with_the_explicit_operator"></a>   
## <a name="explicit-conversion-with-the-explicit-operator"></a>Jawna konwersja za pomocą operatora Explicit  
 Konwersje zawężające obejmują utworzenie nowej wartości z wartości istniejącego typu, która ma większy zakres lub większą listę elementów członkowskich niż typ docelowy. Konwersja zawężająca może spowodować utratę danych, więc kompilatory często wymagają, aby taka konwersja została wykonana jawnie za pomocą wywołania metody konwersji lub operatora rzutowania. Oznacza to, że konwersja musi być jawnie obsługiwana w kodzie dewelopera.  
  
> [!NOTE]
>  Głównym celem wymagania użycia metody konwersji lub operatora rzutowania dla konwersji zawężających jest uświadomienie deweloperowi prawdopodobieństwa utraty danych lub <xref:System.OverflowException> , dzięki czemu mogą być obsługiwane w kodzie. Jednak niektóre kompilatory umożliwiają nieprzestrzeganie tego wymagania. Na przykład w Visual Basic, jeśli `Option Strict` jest wyłączone (ustawienie domyślne), kompilator Visual Basic podejmie próbę niejawnego wykonania konwersji zawężających.  
  
 Na przykład <xref:System.UInt32>, <xref:System.Int64>, i <xref:System.UInt64> typy danych mają zakresy, które <xref:System.Int32> typu danych, jak pokazano w poniższej tabeli.  
  
|Typ|Porównanie z zakresem typu Int32|  
|----------|------------------------------------|  
|<xref:System.Int64>|<xref:System.Int64.MaxValue?displayProperty=nameWithType> jest większa niż <xref:System.Int32.MaxValue?displayProperty=nameWithType>, i <xref:System.Int64.MinValue?displayProperty=nameWithType> jest mniejsza niż (ma większy zakres ujemny niż) <xref:System.Int32.MinValue?displayProperty=nameWithType>.|  
|<xref:System.UInt32>|<xref:System.UInt32.MaxValue?displayProperty=nameWithType> jest większa niż <xref:System.Int32.MaxValue?displayProperty=nameWithType>.|  
|<xref:System.UInt64>|<xref:System.UInt64.MaxValue?displayProperty=nameWithType> jest większa niż <xref:System.Int32.MaxValue?displayProperty=nameWithType>.|  
  
 Aby obsługę takich konwersji zawężających [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] umożliwia typom definiowanie `Explicit` operatora. Kompilatory poszczególnych języków mogą implementować Ten operator, używając własnej składni lub członkiem <xref:System.Convert> klasy można wywołać w celu wykonania konwersji. (Aby uzyskać więcej informacji na temat <xref:System.Convert> klasy, zobacz [klasa Convert](#Convert) w dalszej części tego tematu.) Poniższy przykład ilustruje użycie funkcji języka w celu obsługi jawnej konwersji tych wartości potencjalnie poza zakres liczby całkowitej, aby <xref:System.Int32> wartości.  
  
 [!code-csharp[Conceptual.Conversion#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#4)]
 [!code-vb[Conceptual.Conversion#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#4)]  
  
 Konwersje jawne mogą dawać różne wyniki w różnych językach, a te wyniki mogą się różnić od wartości zwracanej przez odpowiednie <xref:System.Convert> metody. Na przykład jeśli <xref:System.Double> wartość 12.63251 jest konwertowany na <xref:System.Int32>, zarówno języka Visual Basic `CInt` metody i .NET Framework <xref:System.Convert.ToInt32%28System.Double%29?displayProperty=nameWithType> metoda round <xref:System.Double> w celu zwrócenia wartości 13, ale języka C# `(int)` — operator obcina <xref:System.Double> w celu zwrócenia wartości z 12. Podobnie, C# `(int)` operator nie obsługuje konwersji atrybut typu wartość logiczna na całkowite, ale Visual Basic `CInt` metoda konwertuje wartość `true` na -1. Z drugiej strony <xref:System.Convert.ToInt32%28System.Boolean%29?displayProperty=nameWithType> metoda konwertuje wartość `true` 1.  
  
 Większość kompilatorów zezwala na wykonywanie jawnych konwersji w sposób kontrolowany i niekontrolowany. Gdy jest wykonywania konwersja kontrolowana, <xref:System.OverflowException> jest zgłaszany, gdy wartość typu przeznaczonego do konwersji znajduje się poza zakresem typu docelowego. Gdy w tych samych warunkach jest wykonywania konwersja niekontrolowana, konwersja może nie zgłosić wyjątku, ale dokładne zachowanie jest niezdefiniowane i może powstać niepoprawna wartość.  
  
> [!NOTE]
>  W języku C#, zaznaczone konwersje można wykonywać za pomocą `checked` słowa kluczowego, wraz z operatorem rzutowania lub określając `/checked+` — opcja kompilatora. I odwrotnie, konwersje niekontrolowane można wykonać przy użyciu `unchecked` słowa kluczowego, wraz z operatorem rzutowania lub określając `/checked-` — opcja kompilatora. Domyślnie konwersje jawne są niekontrolowane. W języku Visual Basic zaznaczone konwersje można wykonywać, czyszcząc **Usuń nadmiaru** pole wyboru w projekcie **Zaawansowane ustawienia kompilatora** okno dialogowe, albo przez wyszczególnienie `/removeintchecks-`— opcja kompilatora. I odwrotnie, niekontrolowane konwersje można wykonywać przez wybranie **Usuń nadmiaru** pole wyboru w projekcie **Zaawansowane ustawienia kompilatora** okno dialogowe lub określając `/removeintchecks+`— opcja kompilatora. Domyślnie konwersje jawne są kontrolowane.  
  
 Poniższy przykład C# używa `checked` i `unchecked` słów kluczowych w celu pokazania różnicy w zachowaniu, gdy wartość spoza zakresu <xref:System.Byte> jest konwertowana na <xref:System.Byte>. Konwersja kontrolowana zgłasza wyjątek, ale konwersja niekontrolowana przypisuje <xref:System.Byte.MaxValue?displayProperty=nameWithType> do <xref:System.Byte> zmiennej.  
  
 [!code-csharp[Conceptual.Conversion#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#12)]  
  
 Jeśli kompilator danego języka obsługuje niestandardowe operatory przeciążone, konwersje jawne można także definiować we własnych typach niestandardowych. W poniższym przykładzie pokazano częściową implementację typu danych bajtowych ze znakiem o nazwie `ByteWithSign` , który używa reprezentacji logowania i wielkości. Obsługuje jawną konwersję z <xref:System.Int32> i <xref:System.UInt32> wartości `ByteWithSign` wartości.  
  
 [!code-csharp[Conceptual.Conversion#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#5)]
 [!code-vb[Conceptual.Conversion#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#5)]  
  
 Następnie kod klienta może zadeklarować `ByteWithSign` zmiennej i przypisz mu <xref:System.Int32> i <xref:System.UInt32> wartości, jeśli przypisania zawierają operator rzutowania lub metodę konwersji, co ilustruje poniższy przykład.  
  
 [!code-csharp[Conceptual.Conversion#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#6)]
 [!code-vb[Conceptual.Conversion#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#6)]  
  
 [Powrót do początku](#top)  
  
<a name="the_iconvertible_interface"></a>   
## <a name="the-iconvertible-interface"></a>Interfejs IConvertible  
 Do obsługi konwersji dowolnego typu do wspólnego język podstawowy typ środowiska uruchomieniowego, [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] zapewnia <xref:System.IConvertible> interfejsu. Typ implementujący musi dostarczyć następujące elementy:  
  
-   Metoda, która zwraca <xref:System.TypeCode> typu implementującego.  
  
-   Typ metody konwersji implementujący każdego wspólnego typu podstawowego środowiska uruchomieniowego języka (<xref:System.Boolean>, <xref:System.Byte>, <xref:System.DateTime>, <xref:System.Decimal>, <xref:System.Double>i tak dalej).  
  
-   Uogólnioną metodę konwersji służącą do konwertowania wystąpienia typu implementującego na inny określony typ. Konwersje, które nie są obsługiwane powinno zgłosić <xref:System.InvalidCastException>.  
  
 Każdy wspólnego język podstawowy typ środowiska uruchomieniowego (czyli <xref:System.Boolean>, <xref:System.Byte>, <xref:System.Char>, <xref:System.DateTime>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.String>, <xref:System.UInt16>, <xref:System.UInt32>, i <xref:System.UInt64>), a także <xref:System.DBNull> i <xref:System.Enum> typy, implementują <xref:System.IConvertible> interfejsu. Te są jednak jawne implementacje interfejsu; metodę konwersji można wywołać tylko za pośrednictwem <xref:System.IConvertible> zmiennej interfejsu, co ilustruje poniższy przykład. Ten przykład konwertuje <xref:System.Int32> wartość odpowiadającą jej <xref:System.Char> wartość.  
  
 [!code-csharp[Conceptual.Conversion#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible1.cs#7)]
 [!code-vb[Conceptual.Conversion#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible1.vb#7)]  
  
 Wymaganie, aby metoda konwersji była wywoływana w jej interfejsie, a nie w typie implementującym, powoduje, że jawne implementacje interfejsu są relatywnie kosztowne. Zamiast tego zaleca się wywołania odpowiedniej składowej klasy <xref:System.Convert> klasy, aby wykonać konwersję między wspólnej typami podstawowymi środowiska uruchomieniowego języka. Aby uzyskać więcej informacji, zobacz następną sekcję, [klasa Convert](#Convert).  
  
> [!NOTE]
>  Oprócz <xref:System.IConvertible> interfejsu i <xref:System.Convert> dostarczane przez klasy [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], poszczególnych języków mogą być dostępne inne metody wykonywania konwersji. Na przykład C# są używane operatory rzutowania; Visual Basic używa funkcji konwersji implementowane przez kompilator, takich jak `CType`, `CInt`, i `DirectCast`.  
  
 W większości przypadków <xref:System.IConvertible> interfejs jest zaprojektowany do obsługi konwersji między typami podstawowymi w programie [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Jednak ten interfejs może też być implementowany przez typ niestandardowy w celu obsługi konwersji tego typu na inny typ niestandardowy. Aby uzyskać więcej informacji, zobacz sekcję [konwersje niestandardowe z użyciem metody ChangeType](#ChangeType) w dalszej części tego tematu.  
  
 [Powrót do początku](#top)  
  
<a name="Convert"></a>   
## <a name="the-convert-class"></a>Klasa Convert  
 Mimo że każdy typ podstawowy <xref:System.IConvertible> implementacji interfejsu, można wywołać w celu wykonania konwersji typu, wywoływanie metod klasy <xref:System.Convert?displayProperty=nameWithType> klasy jest to zalecany sposób niezależny od języka, aby przekonwertować z jednego typu podstawowego. Ponadto <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metoda może służyć do konwersji z określonego typu niestandardowego do innego typu.  
  
### <a name="conversions-between-base-types"></a>Konwersje między typami podstawowymi  
 <xref:System.Convert> Klasa oferuje językowo neutralny sposób wykonywania konwersji między typami podstawowymi i jest dostępna dla wszystkich języków przeznaczonych dla środowiska uruchomieniowego języka wspólnego. Zapewnia kompletny zestaw metod zarówno konwersji rozszerzających i zawężających i zgłasza <xref:System.InvalidCastException> podczas konwersji, które nie są obsługiwane (np. zamiany <xref:System.DateTime> wartość na wartość całkowitą). Konwersje zawężające są wykonywane w kontekście sprawdzanym i <xref:System.OverflowException> jest generowany, jeśli konwersja nie powiedzie się.  
  
> [!IMPORTANT]
>  Ponieważ <xref:System.Convert> klasa zawiera metody służące do konwersji do i z każdego typu podstawowego, więc eliminuje konieczność wywoływania każdego typu podstawowego <xref:System.IConvertible> jawnej implementacji interfejsu.  
  
 Poniższy przykład ilustruje użycie <xref:System.Convert?displayProperty=nameWithType> klasy w celu wykonania kilku konwersji rozszerzających i zawężających między typami podstawowymi w programie .NET Framework.  
  
 [!code-csharp[Conceptual.Conversion#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#8)]
 [!code-vb[Conceptual.Conversion#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#8)]  
  
 W niektórych przypadkach, szczególnie podczas konwersji do i z wartości zmiennoprzecinkowych, konwersja może spowodować utratę dokładności, nawet jeśli nie zostanie zgłoszony <xref:System.OverflowException>. W poniższym przykładzie pokazano taką utratę dokładności. W pierwszym przypadku <xref:System.Decimal> wartość ma mniejszą dokładność (mniej cyfr znaczących) po przekonwertowaniu na <xref:System.Double>. W drugim przypadku <xref:System.Double> wartość jest zaokrąglana z 42,72 do 43 w celu wykonania konwersji.  
  
 [!code-csharp[Conceptual.Conversion#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#9)]
 [!code-vb[Conceptual.Conversion#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#9)]  
  
 Dla tabeli, która zawiera zarówno rozszerzające i zawężające konwersje obsługiwane przez <xref:System.Convert> klasy, zobacz [tabele konwersji typów](../../../docs/standard/base-types/conversion-tables.md).  
  
<a name="ChangeType"></a>   
### <a name="custom-conversions-with-the-changetype-method"></a>Konwersje niestandardowe z użyciem metody ChangeType  
 Oprócz obsługi konwersji do każdego z typów podstawowych, <xref:System.Convert> klasy może służyć do konwertowania typu niestandardowego na co najmniej jeden wstępnie zdefiniowanych typów. Ta konwersja jest wykonywana przez <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody, która z kolei zawija wywołanie do <xref:System.IConvertible.ToType%2A?displayProperty=nameWithType> metody `value` parametru. Oznacza to, że obiekt reprezentowany przez `value` parametru musi dostarczać implementację <xref:System.IConvertible> interfejsu.  
  
> [!NOTE]
>  Ponieważ <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%29?displayProperty=nameWithType> i <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody za pomocą <xref:System.Type> obiekt do określania typu docelowego, do którego `value` jest konwertowany, ich może służyć do wykonywania dynamicznej konwersji na obiekt, którego typ nie jest znany w czasie kompilacji. Jednak należy pamiętać, że <xref:System.IConvertible> implementacji `value` musi obsługiwać tę konwersję.  
  
 W poniższym przykładzie pokazano możliwą implementację <xref:System.IConvertible> interfejsu, który umożliwia `TemperatureCelsius` obiekt ma zostać przekonwertowane na `TemperatureFahrenheit` obiektu i na odwrót. W przykładzie zdefiniowano klasę bazową `Temperature`, która implementuje <xref:System.IConvertible> interfejsu i zastąpień <xref:System.Object.ToString%2A?displayProperty=nameWithType> metody. Pochodnej `TemperatureCelsius` i `TemperatureFahrenheit` klasy zastępują `ToType` i `ToString` metody klasy bazowej.  
  
 [!code-csharp[Conceptual.Conversion#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#10)]
 [!code-vb[Conceptual.Conversion#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#10)]  
  
 W poniższym przykładzie pokazano kilka wywołań tych <xref:System.IConvertible> implementacji, aby przekonwertować `TemperatureCelsius` obiekty do `TemperatureFahrenheit` obiektów i na odwrót.  
  
 [!code-csharp[Conceptual.Conversion#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#11)]
 [!code-vb[Conceptual.Conversion#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#11)]  
  
 [Powrót do początku](#top)  
  
<a name="the_typeconverter_class"></a>   
## <a name="the-typeconverter-class"></a>Klasa TypeConverter  
 .NET Framework umożliwia także zdefiniowanie konwertera typów dla typu niestandardowego przez rozszerzenie <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType> klasy i skojarzenie konwertera typów z typem za pośrednictwem <xref:System.ComponentModel.TypeConverterAttribute?displayProperty=nameWithType> atrybutu. W poniższej tabeli wymieniono różnice między tym podejściem i wdrażanie <xref:System.IConvertible> interfejsu dla typu niestandardowego.  
  
> [!NOTE]
>  Obsługa typu niestandardowego w czasie projektowania jest możliwa tylko wtedy, gdy zdefiniowano dla niego konwerter typów.  
  
|Konwersja z użyciem klasy TypeConverter|Konwersja z użyciem interfejsu IConvertible|  
|------------------------------------|-----------------------------------|  
|Jest implementowana dla typu niestandardowego przez utworzenie klasy pochodnej klasy z <xref:System.ComponentModel.TypeConverter>. Ta klasa pochodna jest skojarzony z typem niestandardowym przez zastosowanie <xref:System.ComponentModel.TypeConverterAttribute> atrybutu.|Jest implementowana przez typ niestandardowy w celu wykonania konwersji. Użytkownik typu wywołuje <xref:System.IConvertible> metody konwersji typu.|  
|Może być używana w czasie projektowania i w czasie wykonywania.|Może być używana tylko w czasie wykonywania.|  
|Używa odbicia; Dlatego jest wolniejsza niż konwersja przez <xref:System.IConvertible>.|Nie używa odbicia.|  
|Umożliwia dwukierunkowe konwersje typów z typu niestandardowego na inne typy danych i z innych typów danych na typ niestandardowy. Na przykład <xref:System.ComponentModel.TypeConverter> zdefiniowane dla `MyType` umożliwia konwersje z `MyType` do <xref:System.String>i z <xref:System.String> do `MyType`.|Umożliwia konwersję z typu niestandardowego na inne typy danych, ale nie z innych typów danych na typ niestandardowy.|  
  
 Aby uzyskać więcej informacji dotyczących używania konwerterów typów w celu wykonywania konwersji, zobacz <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Convert?displayProperty=nameWithType>  
- <xref:System.IConvertible>  
- [Tabele konwersji typów](../../../docs/standard/base-types/conversion-tables.md)
