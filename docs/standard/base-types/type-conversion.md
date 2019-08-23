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
ms.openlocfilehash: a8fc6f59b7a295cb73489a644da80976345cb172
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922691"
---
# <a name="type-conversion-in-the-net-framework"></a>Konwersja typów w programie .NET Framework
<a name="top"></a>Każda wartość ma skojarzony typ, który definiuje atrybuty, takie jak ilość miejsca przydzieloną do wartości, zakres możliwych wartości, które może mieć, oraz członków, które udostępnia. Wiele wartości można wyrazić za pomocą co najmniej dwóch typów. Na przykład wartość 4 może być wyrażona jako liczba całkowita lub wartość zmiennoprzecinkowa. Konwersja typu tworzy wartość nowego typu, która jest równoważna wartości starego typu, ale nie zawsze powoduje zachowanie tożsamości (dokładnej wartości) oryginalnego obiektu.  
  
 .NET Framework automatycznie obsługuje następujące konwersje:  
  
- Konwersja z klasy pochodnej na klasę bazową. Oznacza to, na przykład, że wystąpienie dowolnej klasy lub struktury można przekonwertować na <xref:System.Object> wystąpienie.  Ta konwersja nie wymaga operatora rzutowania ani konwersji.  
  
- Konwersja z klasy bazowej z powrotem do oryginalnej klasy pochodnej. W C#programie ta konwersja wymaga operatora rzutowania. W Visual Basic wymaga `CType` operatora, jeśli `Option Strict` jest włączony.  
  
- Konwersja z typu, który implementuje interfejs do obiektu interfejsu, który reprezentuje ten interfejs. Ta konwersja nie wymaga operatora rzutowania ani konwersji.  
  
- Konwersja z obiektu interfejsu z powrotem do oryginalnego typu, który implementuje ten interfejs.  W C#programie ta konwersja wymaga operatora rzutowania. W Visual Basic wymaga `CType` operatora, jeśli `Option Strict` jest włączony.  
  
 Oprócz tych automatycznych konwersji .NET Framework udostępnia kilka funkcji, które obsługują konwersję typów niestandardowych. Należą do nich między innymi:  
  
- `Implicit` Operator, który definiuje dostępne rozszerzenia konwersji między typami. Aby uzyskać więcej informacji, zobacz sekcję niejawna [Konwersja z](#implicit_conversion_with_the_implicit_operator) niejawnym operatorem.  
  
- `Explicit` Operator, który definiuje dostępne konwersje wąskie między typami. Aby uzyskać więcej informacji, zobacz [jawna konwersja za pomocą jawnego operatora](#explicit_conversion_with_the_explicit_operator) .  
  
- <xref:System.IConvertible> Interfejs, który definiuje konwersje do poszczególnych typów danych .NET Framework podstawowych. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [interfejsu obiektem IConvertible](#the_iconvertible_interface) .  
  
- Klasa, która dostarcza zestaw metod implementujących metody <xref:System.IConvertible> w interfejsie. <xref:System.Convert> Aby uzyskać więcej informacji, zobacz sekcję [konwertowanie klasy](#Convert) .  
  
- <xref:System.ComponentModel.TypeConverter> Klasa, która jest klasą bazową, która może zostać rozszerzona w celu obsługi konwersji określonego typu do dowolnego innego typu. Aby uzyskać więcej informacji, zobacz sekcję [Klasa TypeConverter](#the_typeconverter_class) .  
  
<a name="implicit_conversion_with_the_implicit_operator"></a>   
## <a name="implicit-conversion-with-the-implicit-operator"></a>Niejawna konwersja za pomocą operatora Implicit  
 Konwersje rozszerzające obejmują utworzenie nowej wartości z wartości istniejącego typu, która ma bardziej ograniczony zakres lub bardziej ograniczoną listę elementów członkowskich niż typ docelowy. Konwersje rozszerzające nie mogą powodować utraty danych (chociaż mogą powodować utratę dokładności). Dane nie mogą być tracone, więc kompilatory mogą obsługiwać konwersję niejawnie (niewidocznie), dzięki czemu użytkownik nie musi używać jawnej metody konwersji ani operatora rzutowania.  
  
> [!NOTE]
> Mimo że kod wywołujący niejawną konwersję może wywołać metodę konwersji lub użyć operatora rzutowania, ich użycie nie jest wymagane przez kompilatory obsługujące konwersje niejawne.  
  
 Na <xref:System.Decimal> przykład typ obsługuje niejawne konwersje z <xref:System.Byte> <xref:System.Int64> <xref:System.Int32> <xref:System.Char> <xref:System.Int16> ,,<xref:System.SByte> ,,<xref:System.UInt64> ,,, i wartości. <xref:System.UInt16> <xref:System.UInt32> Poniższy przykład ilustruje niektóre z tych niejawnych konwersji w przypisywaniu <xref:System.Decimal> wartości do zmiennej.  
  
 [!code-csharp[Conceptual.Conversion#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#1)]
 [!code-vb[Conceptual.Conversion#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#1)]  
  
 Jeśli kompilator określonego języka obsługuje operatory niestandardowe, niejawne konwersje można także definiować we własnych typach niestandardowych. Poniższy przykład zawiera częściową implementację typu danych bajtu ze znakiem `ByteWithSign` o nazwie, która używa reprezentacji i wielkości liter. Obsługuje ona niejawną <xref:System.Byte> konwersję i `ByteWithSign` <xref:System.SByte> wartości na wartości.  
  
 [!code-csharp[Conceptual.Conversion#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#2)]
 [!code-vb[Conceptual.Conversion#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#2)]  
  
 Kod klienta może następnie zadeklarować `ByteWithSign` zmienną i przypisać ją <xref:System.Byte> i <xref:System.SByte> wartości bez wykonywania jakichkolwiek jawnych konwersji lub użycia operatorów rzutowania, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Conceptual.Conversion#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#3)]
 [!code-vb[Conceptual.Conversion#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#3)]  
  
 [Powrót do początku](#top)  
  
<a name="explicit_conversion_with_the_explicit_operator"></a>   
## <a name="explicit-conversion-with-the-explicit-operator"></a>Jawna konwersja za pomocą operatora Explicit  
 Konwersje zawężające obejmują utworzenie nowej wartości z wartości istniejącego typu, która ma większy zakres lub większą listę elementów członkowskich niż typ docelowy. Konwersja zawężająca może spowodować utratę danych, więc kompilatory często wymagają, aby taka konwersja została wykonana jawnie za pomocą wywołania metody konwersji lub operatora rzutowania. Oznacza to, że konwersja musi być jawnie obsługiwana w kodzie dewelopera.  
  
> [!NOTE]
> Głównym celem wymagania metody konwersji lub operatora rzutowania dla konwersji zawężania jest umożliwienie deweloperowi świadomości utraty danych lub <xref:System.OverflowException> , aby można było je obsłużyć w kodzie. Jednak niektóre kompilatory umożliwiają nieprzestrzeganie tego wymagania. Na przykład w Visual Basic, jeśli `Option Strict` jest wyłączony (ustawienie domyślne), kompilator Visual Basic próbuje wykonać konwersje zawęża niejawnie.  
  
 Na przykład <xref:System.UInt32> <xref:System.UInt64> ,, i typy<xref:System.Int32> danych mają zakresy, które przekraczają typ danych, jak pokazano w poniższej tabeli. <xref:System.Int64>  
  
|Typ|Porównanie z zakresem typu Int32|  
|----------|------------------------------------|  
|<xref:System.Int64>|<xref:System.Int64.MaxValue?displayProperty=nameWithType>jest większe niż <xref:System.Int32.MaxValue?displayProperty=nameWithType>i <xref:System.Int64.MinValue?displayProperty=nameWithType> jest mniejsze niż (ma większy zakres ujemny niż) <xref:System.Int32.MinValue?displayProperty=nameWithType>.|  
|<xref:System.UInt32>|<xref:System.UInt32.MaxValue?displayProperty=nameWithType>jest większa niż <xref:System.Int32.MaxValue?displayProperty=nameWithType>.|  
|<xref:System.UInt64>|<xref:System.UInt64.MaxValue?displayProperty=nameWithType>jest większa niż <xref:System.Int32.MaxValue?displayProperty=nameWithType>.|  
  
 Aby obsłużyć takie przekształcenia, .NET Framework zezwala na definiowanie `Explicit` operatora. Kompilatory poszczególnych języków mogą następnie zaimplementować ten operator przy użyciu własnej składni lub można wywołać element członkowski <xref:System.Convert> klasy w celu przeprowadzenia konwersji. (Aby uzyskać więcej informacji na <xref:System.Convert> temat klasy, zobacz [konwertowanie klasy](#Convert) w dalszej części tego tematu). Poniższy przykład ilustruje użycie funkcji języka do obsługi jawnej konwersji tych wartości całkowitych, które potencjalnie poza zakresem, do <xref:System.Int32> wartości.  
  
 [!code-csharp[Conceptual.Conversion#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#4)]
 [!code-vb[Conceptual.Conversion#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#4)]  
  
 Konwersje jawne mogą generować różne wyniki w różnych językach, a wyniki te mogą się różnić od wartości zwracanej przez odpowiednią <xref:System.Convert> metodę. Na przykład <xref:System.Double> Jeśli wartość 12,63251 jest konwertowana na obiekt <xref:System.Int32>, zarówno Metoda Visual Basic `CInt` , jak i Metoda <xref:System.Double> .NET Framework <xref:System.Convert.ToInt32%28System.Double%29?displayProperty=nameWithType> , aby zwracały wartość 13, ale C# `(int)` operator obcina <xref:System.Double> do zwraca wartość 12. Podobnie operator nie obsługuje konwersji typu Boolean na liczbę całkowitą, ale metoda Visual Basic `CInt` konwertuje wartość `true` na-1. `(int)` C# Z drugiej strony <xref:System.Convert.ToInt32%28System.Boolean%29?displayProperty=nameWithType> Metoda konwertuje `true` wartość na 1.  
  
 Większość kompilatorów zezwala na wykonywanie jawnych konwersji w sposób kontrolowany i niekontrolowany. Gdy sprawdzona konwersja jest wykonywana, <xref:System.OverflowException> jest zgłaszany, gdy wartość typu do przekonwertowania znajduje się poza zakresem typu docelowego. Gdy w tych samych warunkach jest wykonywania konwersja niekontrolowana, konwersja może nie zgłosić wyjątku, ale dokładne zachowanie jest niezdefiniowane i może powstać niepoprawna wartość.  
  
> [!NOTE]
> W C#programie sprawdzone konwersje można wykonać za pomocą `checked` słowa kluczowego ze operatorem rzutowania `/checked+` lub określając opcję kompilatora. Z drugiej strony konwersje niesprawdzone można wykonać za pomocą `unchecked` słowa kluczowego ze operatorem rzutowania lub `/checked-` określając opcję kompilatora. Domyślnie konwersje jawne są niekontrolowane. W Visual Basic sprawdzone konwersje można wykonać, czyszcząc pole wyboru **Usuń sprawdzanie przepełnienia liczby całkowitej** w oknie dialogowym **Zaawansowane ustawienia kompilatora** projektu lub określając `/removeintchecks-` opcję kompilatora. Z drugiej strony konwersje niesprawdzone można wykonać, zaznaczając pole wyboru **Usuń sprawdzanie przepełnienia liczby całkowitej** w oknie dialogowym **Zaawansowane ustawienia kompilatora** projektu lub określając `/removeintchecks+` opcję kompilatora. Domyślnie konwersje jawne są kontrolowane.  
  
 W poniższym C# przykładzie używane `checked` są słowa `unchecked` kluczowe i, aby zilustrować różnice w zachowaniu, gdy wartość spoza <xref:System.Byte>zakresu elementu <xref:System.Byte> jest konwertowana na. Sprawdzona konwersja zgłasza wyjątek, ale niesprawdzona konwersja przypisuje <xref:System.Byte.MaxValue?displayProperty=nameWithType> <xref:System.Byte> do zmiennej.  
  
 [!code-csharp[Conceptual.Conversion#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#12)]  
  
 Jeśli kompilator danego języka obsługuje niestandardowe operatory przeciążone, konwersje jawne można także definiować we własnych typach niestandardowych. Poniższy przykład zawiera częściową implementację typu danych bajtu ze znakiem `ByteWithSign` o nazwie, która używa reprezentacji i wielkości liter. Obsługuje ona jawną <xref:System.Int32> konwersję <xref:System.UInt32> i wartości `ByteWithSign` do wartości.  
  
 [!code-csharp[Conceptual.Conversion#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#5)]
 [!code-vb[Conceptual.Conversion#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#5)]  
  
 Kod klienta może następnie zadeklarować `ByteWithSign` zmienną i przypisać ją <xref:System.Int32> i <xref:System.UInt32> wartości, jeśli przypisania zawierają operator rzutowania lub metodę konwersji, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Conceptual.Conversion#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#6)]
 [!code-vb[Conceptual.Conversion#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#6)]  
  
 [Powrót do początku](#top)  
  
<a name="the_iconvertible_interface"></a>   
## <a name="the-iconvertible-interface"></a>Interfejs IConvertible  
 Aby zapewnić obsługę konwersji dowolnego typu na typ podstawowy środowiska uruchomieniowego języka wspólnego, .NET Framework dostarcza <xref:System.IConvertible> interfejs. Typ implementujący musi dostarczyć następujące elementy:  
  
- Metoda zwracająca <xref:System.TypeCode> typ implementujący.  
  
- Metody konwersji typu implementującego na każdy typ podstawowy środowiska uruchomieniowego języka wspólnego<xref:System.Boolean>( <xref:System.Byte>, <xref:System.DateTime>, <xref:System.Decimal> <xref:System.Double>,,, itd.).  
  
- Uogólnioną metodę konwersji służącą do konwertowania wystąpienia typu implementującego na inny określony typ. Konwersje, które nie są obsługiwane, powinny <xref:System.InvalidCastException>zgłosić.  
  
 Każdy typ podstawowy środowiska uruchomieniowego języka wspólnego (to jest <xref:System.Boolean> <xref:System.Decimal> <xref:System.Byte> <xref:System.Double> <xref:System.Char> <xref:System.Int16> <xref:System.DateTime> ,,<xref:System.Int32>,,,,, ,,,<xref:System.SByte> <xref:System.Int64> <xref:System.Single>, <xref:System.String>, <xref:System.UInt16> <xref:System.IConvertible> ,, i<xref:System.UInt64>), a<xref:System.DBNull> także typy i <xref:System.Enum> , implementują interfejs. <xref:System.UInt32> Są to jednak jawne implementacje interfejsu; Metoda konwersji może być wywoływana tylko za pomocą <xref:System.IConvertible> zmiennej interfejsu, jak pokazano w poniższym przykładzie. Ten przykład konwertuje <xref:System.Int32> wartość na jej równoważną <xref:System.Char> wartość.  
  
 [!code-csharp[Conceptual.Conversion#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible1.cs#7)]
 [!code-vb[Conceptual.Conversion#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible1.vb#7)]  
  
 Wymaganie, aby metoda konwersji była wywoływana w jej interfejsie, a nie w typie implementującym, powoduje, że jawne implementacje interfejsu są relatywnie kosztowne. Zamiast tego zalecamy wywołanie odpowiedniej składowej <xref:System.Convert> klasy w celu konwersji między typami podstawowymi środowiska uruchomieniowego języka wspólnego. Aby uzyskać więcej informacji, zobacz następną sekcję [klasy Convert](#Convert).  
  
> [!NOTE]
> Oprócz <xref:System.IConvertible> interfejsu<xref:System.Convert> i klasy dostarczonej przez .NET Framework poszczególne języki mogą również zapewniać sposoby wykonywania konwersji. Na przykład C# używa operatorów rzutowania; Visual Basic używa funkcji konwersji implementowanych przez kompilator, `CType`takich `CInt`jak, `DirectCast`, i.  
  
 W większości, <xref:System.IConvertible> interfejs jest przeznaczony do obsługi konwersji między typami podstawowymi w .NET Framework. Jednak ten interfejs może też być implementowany przez typ niestandardowy w celu obsługi konwersji tego typu na inny typ niestandardowy. Aby uzyskać więcej informacji, zobacz sekcję [konwersje niestandardowe przy użyciu metody ChangeType](#ChangeType) w dalszej części tego tematu.  
  
 [Powrót do początku](#top)  
  
<a name="Convert"></a>   
## <a name="the-convert-class"></a>Klasa Convert  
 Chociaż implementacja <xref:System.IConvertible> interfejsu każdego typu podstawowego może być wywoływana w celu przeprowadzenia konwersji typu, wywoływanie metod <xref:System.Convert?displayProperty=nameWithType> klasy jest zalecanym sposobem konwersji z jednego typu podstawowego na inny. Ponadto <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> Metoda może służyć do konwersji z określonego typu niestandardowego na inny typ.  
  
### <a name="conversions-between-base-types"></a>Konwersje między typami podstawowymi  
 <xref:System.Convert> Klasa zapewnia neutralny językowo sposób wykonywania konwersji między typami podstawowymi i jest dostępny dla wszystkich języków przeznaczonych dla środowiska uruchomieniowego języka wspólnego. Zawiera kompletny zestaw metod zarówno do rozszerzania, jak i zawężania konwersji, i zgłasza <xref:System.InvalidCastException> dla konwersji, które nie są obsługiwane (na przykład konwersja <xref:System.DateTime> wartości do wartości całkowitej). Konwersje wąskie są wykonywane w sprawdzonym kontekście i <xref:System.OverflowException> są generowane, jeśli konwersja nie powiedzie się.  
  
> [!IMPORTANT]
> Ponieważ klasa obejmuje metody do konwersji do i z każdego typu podstawowego, eliminuje konieczność wywołania <xref:System.IConvertible> jawnej implementacji interfejsu każdego typu podstawowego. <xref:System.Convert>  
  
 Poniższy przykład ilustruje użycie <xref:System.Convert?displayProperty=nameWithType> klasy do wykonywania kilku konwersji rozszerzających i zawężających między .NET Framework typami podstawowymi.  
  
 [!code-csharp[Conceptual.Conversion#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#8)]
 [!code-vb[Conceptual.Conversion#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#8)]  
  
 W niektórych przypadkach, zwłaszcza w przypadku konwersji do i z wartości zmiennoprzecinkowych, konwersja może pociągnąć za niego utratę precyzji, nawet jeśli nie generuje <xref:System.OverflowException>. W poniższym przykładzie pokazano taką utratę dokładności. W pierwszym przypadku <xref:System.Decimal> wartość ma mniejszą dokładność (mniejszą liczbę cyfr), gdy jest konwertowana <xref:System.Double>na. W drugim przypadku <xref:System.Double> wartość jest zaokrąglana z 42,72 do 43 w celu ukończenia konwersji.  
  
 [!code-csharp[Conceptual.Conversion#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#9)]
 [!code-vb[Conceptual.Conversion#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#9)]  
  
 Dla tabeli, która zawiera listę rozszerzonych i wąskich konwersji obsługiwanych przez <xref:System.Convert> klasę, zobacz [tabele konwersji typów](../../../docs/standard/base-types/conversion-tables.md).  
  
<a name="ChangeType"></a>   
### <a name="custom-conversions-with-the-changetype-method"></a>Konwersje niestandardowe z użyciem metody ChangeType  
 Oprócz obsługi konwersji do poszczególnych typów podstawowych, <xref:System.Convert> Klasa może służyć do konwersji typu niestandardowego na jeden lub więcej wstępnie zdefiniowanych typów. Ta konwersja jest wykonywana przez <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metodę, która z kolei zawija wywołanie <xref:System.IConvertible.ToType%2A?displayProperty=nameWithType> metody `value` parametru. Oznacza to, że obiekt reprezentowany przez `value` parametr musi zapewniać implementację <xref:System.IConvertible> interfejsu.  
  
> [!NOTE]
> Ponieważ metody <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%29?displayProperty=nameWithType> i <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> używają <xref:System.Type> obiektu do określenia typu docelowego, do którego `value` jest konwertowany, mogą służyć do przeprowadzenia dynamicznej konwersji do obiektu, którego typ nie jest znany w czasie kompilacji. Należy jednak pamiętać, że <xref:System.IConvertible> implementacja programu `value` musi nadal obsługiwać tę konwersję.  
  
 Poniższy przykład ilustruje możliwe implementację <xref:System.IConvertible> interfejsu, który `TemperatureCelsius` umożliwia przekonwertowanie obiektu na `TemperatureFahrenheit` obiekt i odwrotnie. W przykładzie zdefiniowano klasę bazową `Temperature`, która <xref:System.IConvertible> implementuje interfejs i zastępuje <xref:System.Object.ToString%2A?displayProperty=nameWithType> metodę. Klasy pochodne `TemperatureCelsius` i `TemperatureFahrenheit` `ToType` każdy przesłaniają metodyklasybazoweji.`ToString`  
  
 [!code-csharp[Conceptual.Conversion#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#10)]
 [!code-vb[Conceptual.Conversion#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#10)]  
  
 Poniższy przykład ilustruje kilka wywołań tych <xref:System.IConvertible> implementacji, aby przekonwertować `TemperatureCelsius` obiekty na `TemperatureFahrenheit` obiekty i na odwrót.  
  
 [!code-csharp[Conceptual.Conversion#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#11)]
 [!code-vb[Conceptual.Conversion#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#11)]  
  
 [Powrót do początku](#top)  
  
<a name="the_typeconverter_class"></a>   
## <a name="the-typeconverter-class"></a>Klasa TypeConverter  
 .NET Framework umożliwia również zdefiniowanie konwertera typów dla typu niestandardowego przez rozszerzenie <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType> klasy i skojarzenie konwertera typów z typem <xref:System.ComponentModel.TypeConverterAttribute?displayProperty=nameWithType> za pomocą atrybutu. W poniższej tabeli przedstawiono różnice między tym podejściem a implementacją <xref:System.IConvertible> interfejsu dla typu niestandardowego.  
  
> [!NOTE]
> Obsługa typu niestandardowego w czasie projektowania jest możliwa tylko wtedy, gdy zdefiniowano dla niego konwerter typów.  
  
|Konwersja z użyciem klasy TypeConverter|Konwersja z użyciem interfejsu IConvertible|  
|------------------------------------|-----------------------------------|  
|Jest zaimplementowany dla niestandardowego typu przez wyznaczanie oddzielnej klasy od <xref:System.ComponentModel.TypeConverter>. Ta klasa pochodna jest skojarzona z typem niestandardowym <xref:System.ComponentModel.TypeConverterAttribute> przez zastosowanie atrybutu.|Jest implementowana przez typ niestandardowy w celu wykonania konwersji. Użytkownik typu wywołuje <xref:System.IConvertible> metodę konwersji typu.|  
|Może być używana w czasie projektowania i w czasie wykonywania.|Może być używana tylko w czasie wykonywania.|  
|Używa odbicia; w związku z tym jest wolniejsza niż <xref:System.IConvertible>konwersja włączona przez program.|Nie używa odbicia.|  
|Umożliwia dwukierunkowe konwersje typów z typu niestandardowego na inne typy danych i z innych typów danych na typ niestandardowy. Na <xref:System.ComponentModel.TypeConverter> przykład, zdefiniowane dla programu `MyType` zezwala na konwersje `MyType` z <xref:System.String>do, i <xref:System.String> z `MyType`do.|Umożliwia konwersję z typu niestandardowego na inne typy danych, ale nie z innych typów danych na typ niestandardowy.|  
  
 Aby uzyskać więcej informacji o używaniu konwerterów typów do wykonywania <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType>konwersji, zobacz.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Convert?displayProperty=nameWithType>
- <xref:System.IConvertible>
- [Tabele konwersji typów](../../../docs/standard/base-types/conversion-tables.md)
