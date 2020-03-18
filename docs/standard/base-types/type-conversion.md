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
ms.openlocfilehash: 0e88303f2bac2dae90a97f9d2de92af1d2a0f80d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73976491"
---
# <a name="type-conversion-in-the-net-framework"></a>Konwersja typów w programie .NET Framework
Każda wartość ma skojarzony typ, który definiuje atrybuty, takie jak ilość miejsca przydzielonego do wartości, zakres możliwych wartości, które może mieć, i elementy członkowskie, które udostępnia. Wiele wartości można wyrazić za pomocą co najmniej dwóch typów. Na przykład wartość 4 może być wyrażona jako liczba całkowita lub wartość zmiennoprzecinkowa. Konwersja typu tworzy wartość nowego typu, która jest równoważna wartości starego typu, ale nie zawsze powoduje zachowanie tożsamości (dokładnej wartości) oryginalnego obiektu.  
  
 Program .NET Framework automatycznie obsługuje następujące konwersje:  
  
- Konwersja z klasy pochodnej do klasy podstawowej. Oznacza to na przykład, że wystąpienie dowolnej klasy lub struktury <xref:System.Object> można przekonwertować na wystąpienie.  Ta konwersja nie wymaga operatora rzutowania lub konwersji.  
  
- Konwersja z klasy podstawowej z powrotem do oryginalnej klasy pochodnej. W języku C#, ta konwersja wymaga operatora rzutowania. W języku `CType` Visual Basic `Option Strict` wymaga operatora, jeśli jest włączony.  
  
- Konwersja z typu, który implementuje interfejs do obiektu interfejsu, który reprezentuje ten interfejs. Ta konwersja nie wymaga operatora rzutowania lub konwersji.  
  
- Konwersja z obiektu interfejsu z powrotem do oryginalnego typu, który implementuje tego interfejsu.  W języku C#, ta konwersja wymaga operatora rzutowania. W języku `CType` Visual Basic `Option Strict` wymaga operatora, jeśli jest włączony.  
  
 Oprócz tych automatycznych konwersji .NET Framework zawiera kilka funkcji, które obsługują konwersję typu niestandardowego. Należą do nich między innymi:  
  
- Operator, `Implicit` który definiuje dostępne konwersje poszerzenie między typami. Aby uzyskać więcej informacji, zobacz [konwersja niejawna z niejawną sekcją Operator.](#implicit-conversion-with-the-implicit-operator)  
  
- Operator, `Explicit` który definiuje dostępne konwersje zwężające między typami. Aby uzyskać więcej informacji, zobacz [jawne konwersji z jawne operator](#explicit-conversion-with-the-explicit-operator) sekcji.  
  
- Interfejs, <xref:System.IConvertible> który definiuje konwersje do każdego z podstawowych typów danych .NET Framework. Aby uzyskać więcej informacji, zobacz [IConvertible Interface](#the-iconvertible-interface) sekcji.  
  
- Klasa, <xref:System.Convert> która zawiera zestaw metod, które implementują <xref:System.IConvertible> metody w interfejsie. Aby uzyskać więcej informacji, zobacz [Sekcję Konwertuj klasę.](#the-convert-class)  
  
- Klasa, <xref:System.ComponentModel.TypeConverter> która jest klasą podstawową, która może zostać rozszerzona w celu obsługi konwersji określonego typu na inny typ. Aby uzyskać więcej informacji, zobacz [TypeConverter Class](#the-typeconverter-class) sekcji.  

## <a name="implicit-conversion-with-the-implicit-operator"></a>Niejawna konwersja za pomocą operatora Implicit  
 Konwersje rozszerzające obejmują utworzenie nowej wartości z wartości istniejącego typu, która ma bardziej ograniczony zakres lub bardziej ograniczoną listę elementów członkowskich niż typ docelowy. Konwersje rozszerzające nie mogą powodować utraty danych (chociaż mogą powodować utratę dokładności). Dane nie mogą być tracone, więc kompilatory mogą obsługiwać konwersję niejawnie (niewidocznie), dzięki czemu użytkownik nie musi używać jawnej metody konwersji ani operatora rzutowania.  
  
> [!NOTE]
> Mimo że kod wywołujący niejawną konwersję może wywołać metodę konwersji lub użyć operatora rzutowania, ich użycie nie jest wymagane przez kompilatory obsługujące konwersje niejawne.  
  
 Na przykład <xref:System.Decimal> typ obsługuje konwersje <xref:System.Byte> <xref:System.Char>niejawne <xref:System.SByte>z <xref:System.UInt16> <xref:System.UInt32>, <xref:System.UInt64> , <xref:System.Int16>, <xref:System.Int32> <xref:System.Int64>, , , , i wartości. W poniższym przykładzie przedstawiono niektóre z tych niejawnych <xref:System.Decimal> konwersji przypisując wartości do zmiennej.  
  
 [!code-csharp[Conceptual.Conversion#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#1)]
 [!code-vb[Conceptual.Conversion#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#1)]  
  
 Jeśli kompilator określonego języka obsługuje operatory niestandardowe, niejawne konwersje można także definiować we własnych typach niestandardowych. Poniższy przykład zawiera częściową implementację typu `ByteWithSign` danych bajtów podpisanego o nazwie, który używa reprezentacji znaku i wielkości. Obsługuje niejawną <xref:System.Byte> <xref:System.SByte> konwersję `ByteWithSign` i wartości do wartości.  
  
 [!code-csharp[Conceptual.Conversion#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#2)]
 [!code-vb[Conceptual.Conversion#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#2)]  
  
 Kod klienta może `ByteWithSign` następnie zadeklarować <xref:System.Byte> zmienną i przypisać ją i <xref:System.SByte> wartości bez wykonywania żadnych jawnych konwersji lub przy użyciu żadnych operatorów rzutowania, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Conceptual.Conversion#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#3)]
 [!code-vb[Conceptual.Conversion#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#3)]  

## <a name="explicit-conversion-with-the-explicit-operator"></a>Jawna konwersja za pomocą operatora Explicit  
 Konwersje zawężające obejmują utworzenie nowej wartości z wartości istniejącego typu, która ma większy zakres lub większą listę elementów członkowskich niż typ docelowy. Konwersja zawężająca może spowodować utratę danych, więc kompilatory często wymagają, aby taka konwersja została wykonana jawnie za pomocą wywołania metody konwersji lub operatora rzutowania. Oznacza to, że konwersja musi być jawnie obsługiwana w kodzie dewelopera.  
  
> [!NOTE]
> Głównym celem wymagania metody konwersji lub operatora rzutowania do zawężania konwersji jest uświadomienie deweloperowi możliwości utraty danych lub <xref:System.OverflowException> tak, aby można je było obsługiwać w kodzie. Jednak niektóre kompilatory umożliwiają nieprzestrzeganie tego wymagania. Na przykład w języku `Option Strict` Visual Basic, jeśli jest wyłączony (jego ustawienie domyślne), kompilator języka Visual Basic próbuje wykonać konwersje zawężające niejawnie.  
  
 Na przykład <xref:System.UInt32>typy <xref:System.Int64>, <xref:System.UInt64> i typy danych mają <xref:System.Int32> zakresy, które przekraczają typ danych, jak pokazano w poniższej tabeli.  
  
|Typ|Porównanie z zakresem typu Int32|  
|----------|------------------------------------|  
|<xref:System.Int64>|<xref:System.Int64.MaxValue?displayProperty=nameWithType>jest większa <xref:System.Int32.MaxValue?displayProperty=nameWithType>niż <xref:System.Int64.MinValue?displayProperty=nameWithType> , i jest mniejsza niż <xref:System.Int32.MinValue?displayProperty=nameWithType>(ma większy zakres ujemny niż) .|  
|<xref:System.UInt32>|<xref:System.UInt32.MaxValue?displayProperty=nameWithType>jest większa <xref:System.Int32.MaxValue?displayProperty=nameWithType>niż .|  
|<xref:System.UInt64>|<xref:System.UInt64.MaxValue?displayProperty=nameWithType>jest większa <xref:System.Int32.MaxValue?displayProperty=nameWithType>niż .|  
  
 Aby obsłużyć takie konwersje zawężające, .NET `Explicit` Framework umożliwia typy do definiowania operatora. Kompilatory poszczególnych języków można następnie zaimplementować ten <xref:System.Convert> operator przy użyciu własnej składni lub element członkowski klasy można wywołać do wykonania konwersji. (Aby uzyskać więcej <xref:System.Convert> informacji na temat klasy, zobacz [Convert Klasy](#the-convert-class) w dalszej części tego tematu.) W poniższym przykładzie przedstawiono użycie funkcji języka do obsługi jawnej konwersji tych potencjalnie poza <xref:System.Int32> zakresem wartości całkowitych do wartości.  
  
 [!code-csharp[Conceptual.Conversion#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#4)]
 [!code-vb[Conceptual.Conversion#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#4)]  
  
 Jawne konwersje mogą powodować różne wyniki w różnych językach, a te <xref:System.Convert> wyniki mogą różnić się od wartości zwracanej przez odpowiednią metodę. Na przykład jeśli <xref:System.Double> wartość 12.63251 jest <xref:System.Int32>konwertowana na `CInt` , zarówno Visual <xref:System.Convert.ToInt32%28System.Double%29?displayProperty=nameWithType> Basic metody <xref:System.Double> i metody .NET Framework zaokrąglić, aby zwrócić wartość 13, ale operator C# `(int)` <xref:System.Double> obcina, aby zwrócić wartość 12. Podobnie operator Języka `(int)` C# nie obsługuje konwersji logiczno-całkowitej, ale Visual `CInt` Basic metoda konwertuje wartość `true` do -1. Z drugiej strony <xref:System.Convert.ToInt32%28System.Boolean%29?displayProperty=nameWithType> metoda konwertuje `true` wartość na 1.  
  
 Większość kompilatorów zezwala na wykonywanie jawnych konwersji w sposób kontrolowany i niekontrolowany. Po wykonaniu kontrolowanej konwersji jest <xref:System.OverflowException> generowany, gdy wartość typu do konwersji wykracza poza zakres typu docelowego. Gdy w tych samych warunkach jest wykonywania konwersja niekontrolowana, konwersja może nie zgłosić wyjątku, ale dokładne zachowanie jest niezdefiniowane i może powstać niepoprawna wartość.  
  
> [!NOTE]
> W języku C#, sprawdzone konwersje można `checked` wykonać za pomocą słowa kluczowego `/checked+` razem z operatorem rzutowania lub określając opcję kompilatora. Z drugiej strony niezaznaczone konwersje mogą `unchecked` być wykonywane przy użyciu słowa kluczowego `/checked-` razem z operatorem rzutowania lub przez określenie opcji kompilatora. Domyślnie konwersje jawne są niekontrolowane. W języku Visual Basic można wykonać konwersje zaznaczone przez wyczyszczenie pola wyboru **Usuń kontrolki przepełnienia liczb całkowitych** w oknie dialogowym **Zaawansowane ustawienia kompilatora** projektu lub określając opcję `/removeintchecks-` kompilatora. Z drugiej strony niezaznaczone konwersje można wykonać, zaznaczając pole wyboru **Usuń kontrolki przepełnienia liczb całkowitych** w oknie `/removeintchecks+` dialogowym Zaawansowane ustawienia **kompilatora** projektu lub określając opcję kompilatora. Domyślnie konwersje jawne są kontrolowane.  
  
 Poniższy przykład języka `checked` C# `unchecked` używa słów kluczowych i zilustrować różnicę w <xref:System.Byte> zachowaniu, <xref:System.Byte>gdy wartość spoza zakresu a jest konwertowany do . Sprawdzana konwersja zgłasza wyjątek, ale niezaznaczone <xref:System.Byte.MaxValue?displayProperty=nameWithType> konwersji <xref:System.Byte> przypisuje do zmiennej.  
  
 [!code-csharp[Conceptual.Conversion#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#12)]  
  
 Jeśli kompilator danego języka obsługuje niestandardowe operatory przeciążone, konwersje jawne można także definiować we własnych typach niestandardowych. Poniższy przykład zawiera częściową implementację typu `ByteWithSign` danych bajtów podpisanego o nazwie, który używa reprezentacji znaku i wielkości. Obsługuje jawne <xref:System.Int32> konwersji <xref:System.UInt32> i `ByteWithSign` wartości do wartości.  
  
 [!code-csharp[Conceptual.Conversion#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#5)]
 [!code-vb[Conceptual.Conversion#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#5)]  
  
 Kod klienta może `ByteWithSign` następnie zadeklarować <xref:System.Int32> zmienną i przypisać ją i <xref:System.UInt32> wartości, jeśli przypisania zawierają operator rzutowania lub metodę konwersji, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Conceptual.Conversion#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#6)]
 [!code-vb[Conceptual.Conversion#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#6)]  

## <a name="the-iconvertible-interface"></a>Interfejs IConvertible  
 Aby obsługiwać konwersję dowolnego typu do wspólnego języka typu podstawowego, <xref:System.IConvertible> .NET Framework udostępnia interfejs. Typ implementujący musi dostarczyć następujące elementy:  
  
- Metoda, która <xref:System.TypeCode> zwraca typ implementacji.  
  
- Metody konwertowania typu implementującego na każdy typ<xref:System.Boolean>podstawowy <xref:System.Byte> <xref:System.DateTime>czasu <xref:System.Decimal> <xref:System.Double>wykonywania języka wspólnego ( , , , , i tak dalej).  
  
- Uogólnioną metodę konwersji służącą do konwertowania wystąpienia typu implementującego na inny określony typ. Konwersje, które nie są <xref:System.InvalidCastException>obsługiwane należy wrzucić .  
  
 Każdy typ podstawowy w czasie wykonywania <xref:System.Boolean> <xref:System.Byte>języka <xref:System.Char> <xref:System.DateTime>(czyli , <xref:System.Int64>, <xref:System.SByte> <xref:System.Single>, <xref:System.String> <xref:System.UInt16>, <xref:System.UInt32> <xref:System.Decimal> <xref:System.Double>, <xref:System.UInt64>, <xref:System.Int16> <xref:System.Int32>, , <xref:System.Enum> , , <xref:System.IConvertible> , , i ), a także <xref:System.DBNull> i typy, implementują interfejs. Są to jednak implementacje interfejsu jawnego; metoda konwersji może być wywoływana tylko za pośrednictwem zmiennej <xref:System.IConvertible> interfejsu, jak pokazano w poniższym przykładzie. W tym przykładzie <xref:System.Int32> konwertuje wartość na jego wartość równoważną. <xref:System.Char>  
  
 [!code-csharp[Conceptual.Conversion#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible1.cs#7)]
 [!code-vb[Conceptual.Conversion#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible1.vb#7)]  
  
 Wymaganie, aby metoda konwersji była wywoływana w jej interfejsie, a nie w typie implementującym, powoduje, że jawne implementacje interfejsu są relatywnie kosztowne. Zamiast tego zaleca się wywołanie odpowiedniego <xref:System.Convert> elementu członkowskiego klasy do konwersji między typami podstawowymi wykonywania języka wspólnego. Aby uzyskać więcej informacji, zobacz następną sekcję [The Convert Class](#the-convert-class).  
  
> [!NOTE]
> Oprócz <xref:System.IConvertible> interfejsu i <xref:System.Convert> klasy dostarczonych przez .NET Framework poszczególnych języków może również zapewnić sposoby wykonywania konwersji. Na przykład C# używa operatorów rzutowania; Visual Basic używa funkcji konwersji zaimplementowanych `CInt`przez `DirectCast`kompilator, takich jak `CType`, , i .  
  
 W przeważającej części <xref:System.IConvertible> interfejs jest przeznaczony do obsługi konwersji między typami podstawowymi w .NET Framework. Jednak ten interfejs może też być implementowany przez typ niestandardowy w celu obsługi konwersji tego typu na inny typ niestandardowy. Aby uzyskać więcej informacji, zobacz sekcję [Konwersje niestandardowe z ChangeType Metody](#custom-conversions-with-the-changetype-method) w dalszej części tego tematu.

## <a name="the-convert-class"></a>Klasa Convert
 Mimo że implementacja <xref:System.IConvertible> interfejsu każdego typu podstawowego można wywołać do <xref:System.Convert?displayProperty=nameWithType> wykonania konwersji typu, wywołanie metod klasy jest zalecany m.in. Ponadto <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metoda może służyć do konwersji z określonego typu niestandardowego do innego typu.  
  
### <a name="conversions-between-base-types"></a>Konwersje między typami podstawowymi  
 Klasa <xref:System.Convert> zapewnia sposób neutralne dla języka do wykonywania konwersji między typami podstawowymi i jest dostępna dla wszystkich języków, które są przeznaczone dla języka wspólnego wykonywania. Zawiera kompletny zestaw metod dla konwersji rozszerzania i zawężania i <xref:System.InvalidCastException> zgłasza dla konwersji, które nie są obsługiwane <xref:System.DateTime> (takie jak konwersja wartości na wartość całkowitą). Konwersje zawężające są wykonywane w zaznaczonym kontekście, a zostanie <xref:System.OverflowException> ona wygenerowana, jeśli konwersja nie powiedzie się.  
  
> [!IMPORTANT]
> Ponieważ <xref:System.Convert> klasa zawiera metody konwertowania do i z każdego typu podstawowego, eliminuje <xref:System.IConvertible> konieczność wywoływania implementacji interfejsu jawnego każdego typu podstawowego.  
  
 W poniższym przykładzie przedstawiono <xref:System.Convert?displayProperty=nameWithType> użycie klasy do wykonania kilku konwersji rozszerzających i zawężających między typami podstawowymi platformy .NET Framework.  
  
 [!code-csharp[Conceptual.Conversion#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#8)]
 [!code-vb[Conceptual.Conversion#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#8)]  
  
 W niektórych przypadkach, szczególnie podczas konwertowania do i z wartości zmiennoprzecinkowych, konwersja może obejmować utratę precyzji, nawet jeśli nie rzuca <xref:System.OverflowException>. W poniższym przykładzie pokazano taką utratę dokładności. W pierwszym przypadku <xref:System.Decimal> wartość ma mniejszą precyzję (mniej cyfr znaczących), gdy jest konwertowana na . <xref:System.Double> W drugim przypadku <xref:System.Double> wartość jest zaokrąglana z 42,72 do 43 w celu zakończenia konwersji.  
  
 [!code-csharp[Conceptual.Conversion#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#9)]
 [!code-vb[Conceptual.Conversion#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#9)]  
  
 W przypadku tabeli, która zawiera listę konwersji rozszerzających <xref:System.Convert> i zawężających obsługiwanych przez klasę, zobacz [Tabele konwersji typów](../../../docs/standard/base-types/conversion-tables.md).  

### <a name="custom-conversions-with-the-changetype-method"></a>Konwersje niestandardowe z użyciem metody ChangeType  
 Oprócz obsługi konwersji do każdego z typów <xref:System.Convert> podstawowych, klasa może służyć do konwertowania typu niestandardowego na jeden lub więcej wstępnie zdefiniowanych typów. Ta konwersja jest <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> wykonywana przez metodę, która z <xref:System.IConvertible.ToType%2A?displayProperty=nameWithType> kolei `value` otacza wywołanie metody parametru. Oznacza to, że obiekt `value` reprezentowany przez parametr musi <xref:System.IConvertible> zapewnić implementację interfejsu.  
  
> [!NOTE]
> Ponieważ <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%29?displayProperty=nameWithType> i <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody używają <xref:System.Type> obiektu do określenia typu `value` docelowego, na który jest konwertowany, mogą służyć do wykonywania konwersji dynamicznej do obiektu, którego typ nie jest znany w czasie kompilacji. Należy jednak pamiętać, że <xref:System.IConvertible> implementacja `value` musi nadal wspierać tę konwersję.  
  
 Poniższy przykład ilustruje możliwą implementację <xref:System.IConvertible> interfejsu, który umożliwia `TemperatureCelsius` obiekt do konwersji na `TemperatureFahrenheit` obiekt i odwrotnie. W przykładzie definiuje klasę `Temperature`podstawową, który <xref:System.IConvertible> implementuje interfejs <xref:System.Object.ToString%2A?displayProperty=nameWithType> i zastępuje metodę. Pochodne `TemperatureCelsius` i `TemperatureFahrenheit` klasy każdy `ToType` zastąpić `ToString` i metody klasy podstawowej.  
  
 [!code-csharp[Conceptual.Conversion#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#10)]
 [!code-vb[Conceptual.Conversion#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#10)]  
  
 W poniższym przykładzie przedstawiono <xref:System.IConvertible> kilka wywołań `TemperatureCelsius` tych `TemperatureFahrenheit` implementacji do konwersji obiektów do obiektów i odwrotnie.  
  
 [!code-csharp[Conceptual.Conversion#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#11)]
 [!code-vb[Conceptual.Conversion#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#11)]  

## <a name="the-typeconverter-class"></a>Klasa TypeConverter  
 .NET Framework umożliwia również zdefiniowanie konwertera typów <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType> dla typu niestandardowego przez rozszerzenie klasy i kojarzenie konwertera typów z typem za pomocą atrybutu. <xref:System.ComponentModel.TypeConverterAttribute?displayProperty=nameWithType> W poniższej tabeli wyróżniono różnice <xref:System.IConvertible> między tym podejściem a implementowaniem interfejsu dla typu niestandardowego.  
  
> [!NOTE]
> Obsługa typu niestandardowego w czasie projektowania jest możliwa tylko wtedy, gdy zdefiniowano dla niego konwerter typów.  
  
|Konwersja z użyciem klasy TypeConverter|Konwersja z użyciem interfejsu IConvertible|  
|------------------------------------|-----------------------------------|  
|Jest zaimplementowana dla typu niestandardowego przez <xref:System.ComponentModel.TypeConverter>wyprowadzenie oddzielnej klasy z . Ta klasa pochodna jest skojarzona <xref:System.ComponentModel.TypeConverterAttribute> z typem niestandardowym przez zastosowanie atrybutu.|Jest implementowana przez typ niestandardowy w celu wykonania konwersji. Użytkownik tego typu wywołuje <xref:System.IConvertible> metodę konwersji na typ.|  
|Może być używana w czasie projektowania i w czasie wykonywania.|Może być używana tylko w czasie wykonywania.|  
|Używa odbicia; w związku z tym jest <xref:System.IConvertible>wolniejszy niż konwersja włączona przez .|Nie używa odbicia.|  
|Umożliwia dwukierunkowe konwersje typów z typu niestandardowego na inne typy danych i z innych typów danych na typ niestandardowy. Na przykład <xref:System.ComponentModel.TypeConverter> zdefiniowane dla `MyType` umożliwia `MyType` konwersje <xref:System.String>z <xref:System.String> do `MyType`, i z do .|Umożliwia konwersję z typu niestandardowego na inne typy danych, ale nie z innych typów danych na typ niestandardowy.|  
  
 Aby uzyskać więcej informacji na temat używania <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType>konwerterów typów do wykonywania konwersji, zobacz .  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Convert?displayProperty=nameWithType>
- <xref:System.IConvertible>
- [Tabele konwersji typów](../../../docs/standard/base-types/conversion-tables.md)
