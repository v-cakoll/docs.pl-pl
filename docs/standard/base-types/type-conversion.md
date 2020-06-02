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
ms.openlocfilehash: 33b8c49033c901917e674879048558799f484194
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291659"
---
# <a name="type-conversion-in-the-net-framework"></a>Konwersja typów w programie .NET Framework
Każda wartość ma skojarzony typ, który definiuje atrybuty, takie jak ilość miejsca przydzieloną do wartości, zakres możliwych wartości, które może mieć, oraz członków, które udostępnia. Wiele wartości można wyrazić za pomocą co najmniej dwóch typów. Na przykład wartość 4 może być wyrażona jako liczba całkowita lub wartość zmiennoprzecinkowa. Konwersja typu tworzy wartość nowego typu, która jest równoważna wartości starego typu, ale nie zawsze powoduje zachowanie tożsamości (dokładnej wartości) oryginalnego obiektu.  
  
 .NET Framework automatycznie obsługuje następujące konwersje:  
  
- Konwersja z klasy pochodnej na klasę bazową. Oznacza to, na przykład, że wystąpienie dowolnej klasy lub struktury można przekonwertować na <xref:System.Object> wystąpienie.  Ta konwersja nie wymaga operatora rzutowania ani konwersji.  
  
- Konwersja z klasy bazowej z powrotem do oryginalnej klasy pochodnej. W języku C# ta konwersja wymaga operatora rzutowania. W Visual Basic wymaga `CType` operatora, jeśli `Option Strict` jest włączony.  
  
- Konwersja z typu, który implementuje interfejs do obiektu interfejsu, który reprezentuje ten interfejs. Ta konwersja nie wymaga operatora rzutowania ani konwersji.  
  
- Konwersja z obiektu interfejsu z powrotem do oryginalnego typu, który implementuje ten interfejs.  W języku C# ta konwersja wymaga operatora rzutowania. W Visual Basic wymaga `CType` operatora, jeśli `Option Strict` jest włączony.  
  
 Oprócz tych automatycznych konwersji .NET Framework udostępnia kilka funkcji, które obsługują konwersję typów niestandardowych. Należą do nich między innymi:  
  
- `Implicit`Operator, który definiuje dostępne rozszerzenia konwersji między typami. Aby uzyskać więcej informacji, zobacz sekcję [niejawna konwersja z niejawnym operatorem](#implicit-conversion-with-the-implicit-operator) .  
  
- `Explicit`Operator, który definiuje dostępne konwersje wąskie między typami. Aby uzyskać więcej informacji, zobacz [jawna konwersja za pomocą jawnego operatora](#explicit-conversion-with-the-explicit-operator) .  
  
- <xref:System.IConvertible>Interfejs, który definiuje konwersje do poszczególnych typów danych .NET Framework podstawowych. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [interfejsu obiektem IConvertible](#the-iconvertible-interface) .  
  
- <xref:System.Convert>Klasa, która dostarcza zestaw metod implementujących metody w <xref:System.IConvertible> interfejsie. Aby uzyskać więcej informacji, zobacz sekcję [konwertowanie klasy](#the-convert-class) .  
  
- <xref:System.ComponentModel.TypeConverter>Klasa, która jest klasą bazową, która może zostać rozszerzona w celu obsługi konwersji określonego typu do dowolnego innego typu. Aby uzyskać więcej informacji, zobacz sekcję [Klasa TypeConverter](#the-typeconverter-class) .  

## <a name="implicit-conversion-with-the-implicit-operator"></a>Niejawna konwersja za pomocą operatora Implicit  
 Konwersje rozszerzające obejmują utworzenie nowej wartości z wartości istniejącego typu, która ma bardziej ograniczony zakres lub bardziej ograniczoną listę elementów członkowskich niż typ docelowy. Konwersje rozszerzające nie mogą powodować utraty danych (chociaż mogą powodować utratę dokładności). Dane nie mogą być tracone, więc kompilatory mogą obsługiwać konwersję niejawnie (niewidocznie), dzięki czemu użytkownik nie musi używać jawnej metody konwersji ani operatora rzutowania.  
  
> [!NOTE]
> Mimo że kod wywołujący niejawną konwersję może wywołać metodę konwersji lub użyć operatora rzutowania, ich użycie nie jest wymagane przez kompilatory obsługujące konwersje niejawne.  
  
 Na przykład <xref:System.Decimal> Typ obsługuje niejawne konwersje z,,,,,,, <xref:System.Byte> <xref:System.Char> <xref:System.Int16> <xref:System.Int32> <xref:System.Int64> <xref:System.SByte> <xref:System.UInt16> <xref:System.UInt32> i <xref:System.UInt64> wartości. Poniższy przykład ilustruje niektóre z tych niejawnych konwersji w przypisywaniu wartości do <xref:System.Decimal> zmiennej.  
  
 [!code-csharp[Conceptual.Conversion#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#1)]
 [!code-vb[Conceptual.Conversion#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#1)]  
  
 Jeśli kompilator określonego języka obsługuje operatory niestandardowe, niejawne konwersje można także definiować we własnych typach niestandardowych. Poniższy przykład zawiera częściową implementację typu danych bajtu ze znakiem o nazwie `ByteWithSign` , która używa reprezentacji i wielkości liter. Obsługuje ona niejawną konwersję <xref:System.Byte> i <xref:System.SByte> wartości na `ByteWithSign` wartości.  
  
 [!code-csharp[Conceptual.Conversion#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#2)]
 [!code-vb[Conceptual.Conversion#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#2)]  
  
 Kod klienta może następnie zadeklarować `ByteWithSign` zmienną i przypisać ją <xref:System.Byte> i <xref:System.SByte> wartości bez wykonywania jakichkolwiek jawnych konwersji lub użycia operatorów rzutowania, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Conceptual.Conversion#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#3)]
 [!code-vb[Conceptual.Conversion#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#3)]  

## <a name="explicit-conversion-with-the-explicit-operator"></a>Jawna konwersja za pomocą operatora Explicit  
 Konwersje zawężające obejmują utworzenie nowej wartości z wartości istniejącego typu, która ma większy zakres lub większą listę elementów członkowskich niż typ docelowy. Konwersja zawężająca może spowodować utratę danych, więc kompilatory często wymagają, aby taka konwersja została wykonana jawnie za pomocą wywołania metody konwersji lub operatora rzutowania. Oznacza to, że konwersja musi być jawnie obsługiwana w kodzie dewelopera.  
  
> [!NOTE]
> Głównym celem wymagania metody konwersji lub operatora rzutowania dla konwersji zawężania jest umożliwienie deweloperowi świadomości utraty danych lub, <xref:System.OverflowException> Aby można było je obsłużyć w kodzie. Jednak niektóre kompilatory umożliwiają nieprzestrzeganie tego wymagania. Na przykład w Visual Basic, jeśli `Option Strict` jest wyłączony (ustawienie domyślne), kompilator Visual Basic próbuje wykonać konwersje zawęża niejawnie.  
  
 Na przykład, <xref:System.UInt32> <xref:System.Int64> , i <xref:System.UInt64> typy danych mają zakresy, które przekraczają <xref:System.Int32> Typ danych, jak pokazano w poniższej tabeli.  
  
|Typ|Porównanie z zakresem typu Int32|  
|----------|------------------------------------|  
|<xref:System.Int64>|<xref:System.Int64.MaxValue?displayProperty=nameWithType>jest większe niż <xref:System.Int32.MaxValue?displayProperty=nameWithType> i <xref:System.Int64.MinValue?displayProperty=nameWithType> jest mniejsze niż (ma większy zakres ujemny niż) <xref:System.Int32.MinValue?displayProperty=nameWithType> .|  
|<xref:System.UInt32>|<xref:System.UInt32.MaxValue?displayProperty=nameWithType>jest większa niż <xref:System.Int32.MaxValue?displayProperty=nameWithType> .|  
|<xref:System.UInt64>|<xref:System.UInt64.MaxValue?displayProperty=nameWithType>jest większa niż <xref:System.Int32.MaxValue?displayProperty=nameWithType> .|  
  
 Aby obsłużyć takie przekształcenia, .NET Framework zezwala na definiowanie `Explicit` operatora. Kompilatory poszczególnych języków mogą następnie zaimplementować ten operator przy użyciu własnej składni lub <xref:System.Convert> można wywołać element członkowski klasy w celu przeprowadzenia konwersji. (Aby uzyskać więcej informacji na temat <xref:System.Convert> klasy, zobacz [konwertowanie klasy](#the-convert-class) w dalszej części tego tematu). Poniższy przykład ilustruje użycie funkcji języka do obsługi jawnej konwersji tych wartości całkowitych, które potencjalnie poza zakresem, do <xref:System.Int32> wartości.  
  
 [!code-csharp[Conceptual.Conversion#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#4)]
 [!code-vb[Conceptual.Conversion#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#4)]  
  
 Konwersje jawne mogą generować różne wyniki w różnych językach, a wyniki te mogą się różnić od wartości zwracanej przez odpowiednią <xref:System.Convert> metodę. Na przykład jeśli <xref:System.Double> wartość 12,63251 jest konwertowana na obiekt <xref:System.Int32> , zarówno Metoda Visual Basic, `CInt` jak i metoda .NET Framework, <xref:System.Convert.ToInt32%28System.Double%29?displayProperty=nameWithType> <xref:System.Double> aby zwracały wartość 13, ale operator języka C# obcina wartość w `(int)` <xref:System.Double> celu zwrócenia wartości 12. Podobnie operator języka C# nie `(int)` obsługuje konwersji typu Boolean na liczbę całkowitą, ale `CInt` Metoda Visual Basic konwertuje wartość `true` na-1. Z drugiej strony <xref:System.Convert.ToInt32%28System.Boolean%29?displayProperty=nameWithType> Metoda konwertuje wartość `true` na 1.  
  
 Większość kompilatorów zezwala na wykonywanie jawnych konwersji w sposób kontrolowany i niekontrolowany. Gdy sprawdzona konwersja jest wykonywana, <xref:System.OverflowException> jest zgłaszany, gdy wartość typu do przekonwertowania znajduje się poza zakresem typu docelowego. Gdy w tych samych warunkach jest wykonywania konwersja niekontrolowana, konwersja może nie zgłosić wyjątku, ale dokładne zachowanie jest niezdefiniowane i może powstać niepoprawna wartość.  
  
> [!NOTE]
> W języku C# sprawdzono konwersje można wykonać za pomocą `checked` słowa kluczowego ze operatorem rzutowania lub określając `/checked+` opcję kompilatora. Z drugiej strony konwersje niesprawdzone można wykonać za pomocą `unchecked` słowa kluczowego ze operatorem rzutowania lub określając `/checked-` opcję kompilatora. Domyślnie konwersje jawne są niekontrolowane. W Visual Basic sprawdzone konwersje można wykonać, czyszcząc pole wyboru **Usuń sprawdzanie przepełnienia liczby całkowitej** w oknie dialogowym **Zaawansowane ustawienia kompilatora** projektu lub określając `/removeintchecks-` opcję kompilatora. Z drugiej strony konwersje niesprawdzone można wykonać, zaznaczając pole wyboru **Usuń sprawdzanie przepełnienia liczby całkowitej** w oknie dialogowym **Zaawansowane ustawienia kompilatora** projektu lub określając `/removeintchecks+` opcję kompilatora. Domyślnie konwersje jawne są kontrolowane.  
  
 W poniższym przykładzie w języku C# są używane `checked` `unchecked` słowa kluczowe i, które ilustrują różnice w zachowaniu, gdy wartość spoza zakresu elementu <xref:System.Byte> jest konwertowana na <xref:System.Byte> . Sprawdzona konwersja zgłasza wyjątek, ale niesprawdzona konwersja przypisuje <xref:System.Byte.MaxValue?displayProperty=nameWithType> do <xref:System.Byte> zmiennej.  
  
 [!code-csharp[Conceptual.Conversion#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#12)]  
  
 Jeśli kompilator danego języka obsługuje niestandardowe operatory przeciążone, konwersje jawne można także definiować we własnych typach niestandardowych. Poniższy przykład zawiera częściową implementację typu danych bajtu ze znakiem o nazwie `ByteWithSign` , która używa reprezentacji i wielkości liter. Obsługuje ona jawną konwersję <xref:System.Int32> i <xref:System.UInt32> wartości do `ByteWithSign` wartości.  
  
 [!code-csharp[Conceptual.Conversion#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#5)]
 [!code-vb[Conceptual.Conversion#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#5)]  
  
 Kod klienta może następnie zadeklarować `ByteWithSign` zmienną i przypisać ją <xref:System.Int32> i <xref:System.UInt32> wartości, jeśli przypisania zawierają operator rzutowania lub metodę konwersji, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Conceptual.Conversion#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#6)]
 [!code-vb[Conceptual.Conversion#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#6)]  

## <a name="the-iconvertible-interface"></a>Interfejs IConvertible  
 Aby zapewnić obsługę konwersji dowolnego typu na typ podstawowy środowiska uruchomieniowego języka wspólnego, .NET Framework dostarcza <xref:System.IConvertible> interfejs. Typ implementujący musi dostarczyć następujące elementy:  
  
- Metoda zwracająca <xref:System.TypeCode> Typ implementujący.  
  
- Metody konwersji typu implementującego na każdy typ podstawowy środowiska uruchomieniowego języka wspólnego ( <xref:System.Boolean> ,,,, <xref:System.Byte> , itd <xref:System.DateTime> <xref:System.Decimal> <xref:System.Double> .).  
  
- Uogólnioną metodę konwersji służącą do konwertowania wystąpienia typu implementującego na inny określony typ. Konwersje, które nie są obsługiwane, powinny zgłosić <xref:System.InvalidCastException> .  
  
 Każdy typ podstawowy środowiska uruchomieniowego języka wspólnego (to,,,,,,,,,,,,,,,,,,,, <xref:System.Boolean> <xref:System.Byte> <xref:System.Char> <xref:System.DateTime> <xref:System.Decimal> <xref:System.Double> <xref:System.Int16> <xref:System.Int32> <xref:System.Int64> <xref:System.SByte> <xref:System.Single> <xref:System.String> <xref:System.UInt16> <xref:System.UInt32> i <xref:System.UInt64> ), <xref:System.DBNull> a także <xref:System.Enum> typy i implementują <xref:System.IConvertible> interfejs. Są to jednak jawne implementacje interfejsu; Metoda konwersji może być wywoływana tylko za pomocą <xref:System.IConvertible> zmiennej interfejsu, jak pokazano w poniższym przykładzie. Ten przykład konwertuje <xref:System.Int32> wartość na jej równoważną <xref:System.Char> wartość.  
  
 [!code-csharp[Conceptual.Conversion#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible1.cs#7)]
 [!code-vb[Conceptual.Conversion#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible1.vb#7)]  
  
 Wymaganie, aby metoda konwersji była wywoływana w jej interfejsie, a nie w typie implementującym, powoduje, że jawne implementacje interfejsu są relatywnie kosztowne. Zamiast tego zalecamy wywołanie odpowiedniej składowej <xref:System.Convert> klasy w celu konwersji między typami podstawowymi środowiska uruchomieniowego języka wspólnego. Aby uzyskać więcej informacji, zobacz następną sekcję [klasy Convert](#the-convert-class).  
  
> [!NOTE]
> Oprócz <xref:System.IConvertible> interfejsu i <xref:System.Convert> klasy dostarczonej przez .NET Framework poszczególne języki mogą również zapewniać sposoby wykonywania konwersji. Na przykład w języku C# są stosowane Operatory rzutowania; Visual Basic używa funkcji konwersji implementowanych przez kompilator, takich jak `CType` , `CInt` , i `DirectCast` .  
  
 W większości, <xref:System.IConvertible> interfejs jest przeznaczony do obsługi konwersji między typami podstawowymi w .NET Framework. Jednak ten interfejs może też być implementowany przez typ niestandardowy w celu obsługi konwersji tego typu na inny typ niestandardowy. Aby uzyskać więcej informacji, zobacz sekcję [konwersje niestandardowe przy użyciu metody ChangeType](#custom-conversions-with-the-changetype-method) w dalszej części tego tematu.

## <a name="the-convert-class"></a>Klasa Convert
 Chociaż implementacja interfejsu każdego typu podstawowego <xref:System.IConvertible> może być wywoływana w celu przeprowadzenia konwersji typu, wywoływanie metod <xref:System.Convert?displayProperty=nameWithType> klasy jest zalecanym sposobem konwersji z jednego typu podstawowego na inny. Ponadto <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> Metoda może służyć do konwersji z określonego typu niestandardowego na inny typ.  
  
### <a name="conversions-between-base-types"></a>Konwersje między typami podstawowymi  
 <xref:System.Convert>Klasa zapewnia neutralny językowo sposób wykonywania konwersji między typami podstawowymi i jest dostępny dla wszystkich języków przeznaczonych dla środowiska uruchomieniowego języka wspólnego. Zawiera kompletny zestaw metod zarówno do rozszerzania, jak i zawężania konwersji, i zgłasza <xref:System.InvalidCastException> dla konwersji, które nie są obsługiwane (na przykład konwersja <xref:System.DateTime> wartości do wartości całkowitej). Konwersje wąskie są wykonywane w sprawdzonym kontekście i <xref:System.OverflowException> są generowane, jeśli konwersja nie powiedzie się.  
  
> [!IMPORTANT]
> Ponieważ <xref:System.Convert> Klasa obejmuje metody do konwersji do i z każdego typu podstawowego, eliminuje konieczność wywołania <xref:System.IConvertible> jawnej implementacji interfejsu każdego typu podstawowego.  
  
 Poniższy przykład ilustruje użycie <xref:System.Convert?displayProperty=nameWithType> klasy do wykonywania kilku konwersji rozszerzających i zawężających między .NET Framework typami podstawowymi.  
  
 [!code-csharp[Conceptual.Conversion#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#8)]
 [!code-vb[Conceptual.Conversion#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#8)]  
  
 W niektórych przypadkach, zwłaszcza w przypadku konwersji do i z wartości zmiennoprzecinkowych, konwersja może pociągnąć za niego utratę precyzji, nawet jeśli nie generuje <xref:System.OverflowException> . W poniższym przykładzie pokazano taką utratę dokładności. W pierwszym przypadku <xref:System.Decimal> wartość ma mniejszą dokładność (mniejszą liczbę cyfr), gdy jest konwertowana na <xref:System.Double> . W drugim przypadku <xref:System.Double> wartość jest zaokrąglana z 42,72 do 43 w celu ukończenia konwersji.  
  
 [!code-csharp[Conceptual.Conversion#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#9)]
 [!code-vb[Conceptual.Conversion#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#9)]  
  
 Dla tabeli, która zawiera listę rozszerzonych i wąskich konwersji obsługiwanych przez <xref:System.Convert> klasę, zobacz [tabele konwersji typów](conversion-tables.md).  

### <a name="custom-conversions-with-the-changetype-method"></a>Konwersje niestandardowe z użyciem metody ChangeType  
 Oprócz obsługi konwersji do poszczególnych typów podstawowych, <xref:System.Convert> Klasa może służyć do konwersji typu niestandardowego na jeden lub więcej wstępnie zdefiniowanych typów. Ta konwersja jest wykonywana przez <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metodę, która z kolei zawija wywołanie <xref:System.IConvertible.ToType%2A?displayProperty=nameWithType> metody `value` parametru. Oznacza to, że obiekt reprezentowany przez `value` parametr musi zapewniać implementację <xref:System.IConvertible> interfejsu.  
  
> [!NOTE]
> Ponieważ <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%29?displayProperty=nameWithType> metody i <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> używają <xref:System.Type> obiektu do określenia typu docelowego, do którego `value` jest konwertowany, mogą służyć do przeprowadzenia dynamicznej konwersji do obiektu, którego typ nie jest znany w czasie kompilacji. Należy jednak pamiętać, że <xref:System.IConvertible> Implementacja programu `value` musi nadal obsługiwać tę konwersję.  
  
 Poniższy przykład ilustruje możliwe implementację <xref:System.IConvertible> interfejsu, który umożliwia `TemperatureCelsius` przekonwertowanie obiektu na `TemperatureFahrenheit` obiekt i odwrotnie. W przykładzie zdefiniowano klasę bazową, `Temperature` która implementuje <xref:System.IConvertible> interfejs i zastępuje <xref:System.Object.ToString%2A?displayProperty=nameWithType> metodę. Klasy pochodne `TemperatureCelsius` i `TemperatureFahrenheit` każdy przesłaniają `ToType` `ToString` metody klasy bazowej i.  
  
 [!code-csharp[Conceptual.Conversion#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#10)]
 [!code-vb[Conceptual.Conversion#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#10)]  
  
 Poniższy przykład ilustruje kilka wywołań tych implementacji, <xref:System.IConvertible> Aby przekonwertować `TemperatureCelsius` obiekty na `TemperatureFahrenheit` obiekty i na odwrót.  
  
 [!code-csharp[Conceptual.Conversion#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#11)]
 [!code-vb[Conceptual.Conversion#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#11)]  

## <a name="the-typeconverter-class"></a>Klasa TypeConverter  
 .NET Framework umożliwia również zdefiniowanie konwertera typów dla typu niestandardowego przez rozszerzenie <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType> klasy i skojarzenie konwertera typów z typem za pomocą <xref:System.ComponentModel.TypeConverterAttribute?displayProperty=nameWithType> atrybutu. W poniższej tabeli przedstawiono różnice między tym podejściem a implementacją <xref:System.IConvertible> interfejsu dla typu niestandardowego.  
  
> [!NOTE]
> Obsługa typu niestandardowego w czasie projektowania jest możliwa tylko wtedy, gdy zdefiniowano dla niego konwerter typów.  
  
|Konwersja z użyciem klasy TypeConverter|Konwersja z użyciem interfejsu IConvertible|  
|------------------------------------|-----------------------------------|  
|Jest zaimplementowany dla niestandardowego typu przez wyznaczanie oddzielnej klasy od <xref:System.ComponentModel.TypeConverter> . Ta klasa pochodna jest skojarzona z typem niestandardowym przez zastosowanie <xref:System.ComponentModel.TypeConverterAttribute> atrybutu.|Jest implementowana przez typ niestandardowy w celu wykonania konwersji. Użytkownik typu wywołuje <xref:System.IConvertible> metodę konwersji typu.|  
|Może być używana w czasie projektowania i w czasie wykonywania.|Może być używana tylko w czasie wykonywania.|  
|Używa odbicia; w związku z tym jest wolniejsza niż konwersja włączona przez program <xref:System.IConvertible> .|Nie używa odbicia.|  
|Umożliwia dwukierunkowe konwersje typów z typu niestandardowego na inne typy danych i z innych typów danych na typ niestandardowy. Na przykład, <xref:System.ComponentModel.TypeConverter> zdefiniowane dla programu `MyType` zezwala na konwersje z `MyType` do <xref:System.String> , i z <xref:System.String> do `MyType` .|Umożliwia konwersję z typu niestandardowego na inne typy danych, ale nie z innych typów danych na typ niestandardowy.|  
  
 Aby uzyskać więcej informacji o używaniu konwerterów typów do wykonywania konwersji, zobacz <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType> .  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Convert?displayProperty=nameWithType>
- <xref:System.IConvertible>
- [Tabele konwersji typów](conversion-tables.md)
