---
title: "Konwersja typów w programie .NET Framework"
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
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 643a1c7d8dd141a8d898af61ba8302f46207321b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="type-conversion-in-the-net-framework"></a>Konwersja typów w programie .NET Framework
<a name="top"></a>Każda wartość ma skojarzony typ, który definiuje atrybuty, takie jak ilość miejsca przydzielonego na wartość zakresu możliwych wartości, który może mieć i elementów członkowskich, dla którego nie udostępnia. Wiele wartości można wyrazić za pomocą co najmniej dwóch typów. Na przykład wartość 4 może być wyrażona jako liczba całkowita lub wartość zmiennoprzecinkowa. Konwersja typu tworzy wartość nowego typu, która jest równoważna wartości starego typu, ale nie zawsze powoduje zachowanie tożsamości (dokładnej wartości) oryginalnego obiektu.  
  
 .NET Framework automatycznie obsługuje następujące konwersji:  
  
-   Konwersja z klasy pochodnej do klasy podstawowej. Oznacza to, na przykład można przekonwertować na wystąpienie klasy lub struktury <xref:System.Object> wystąpienia.  Ta konwersja wymaga operatora rzutowania lub konwersji.  
  
-   Konwersja z klasy podstawowej z powrotem do oryginalnego klasy pochodnej. W języku C# ta konwersja wymaga operatora rzutowania. W języku Visual Basic, wymaga `CType` operator Jeśli `Option Strict` znajduje się na.  
  
-   Konwersja z typu, który implementuje interfejs do obiektu interfejsu, który reprezentuje tego interfejsu. Ta konwersja wymaga operatora rzutowania lub konwersji.  
  
-   Konwersja z obiektu interfejsu z powrotem do oryginalnego typu, który implementuje ten interfejs.  W języku C# ta konwersja wymaga operatora rzutowania. W języku Visual Basic, wymaga `CType` operator Jeśli `Option Strict` znajduje się na.  
  
 Oprócz tych automatycznej konwersji [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] zawiera kilka funkcji, które obsługuje konwersji typu niestandardowego. Należą do nich między innymi:  
  
-   `Implicit` Operatora, który definiuje dostępne poszerzanie konwersji między typami. Aby uzyskać więcej informacji, zobacz [niejawna konwersja z niejawny Operator](#implicit_conversion_with_the_implicit_operator) sekcji.  
  
-   `Explicit` Operatora, który definiuje dostępne konwersji zawężającej między typami. Aby uzyskać więcej informacji, zobacz [jawnej konwersji z operatorem jawne](#explicit_conversion_with_the_explicit_operator) sekcji.  
  
-   <xref:System.IConvertible> Interfejs, który definiuje konwersje do każdego z typów podstawowych danych .NET Framework. Aby uzyskać więcej informacji, zobacz [interfejs IConvertible](#the_iconvertible_interface) sekcji.  
  
-   <xref:System.Convert> Klasy, która udostępnia zestaw metod, które implementują metody w <xref:System.IConvertible> interfejsu. Aby uzyskać więcej informacji, zobacz[klasy przekonwertować](#Convert) sekcji.  
  
-   <xref:System.ComponentModel.TypeConverter> Klasy, która jest klasą podstawową, która może zostać rozszerzony do obsługuje konwersji o określonym typie, do żadnego innego typu. Aby uzyskać więcej informacji, zobacz [klasy TypeConverter](#the_typeconverter_class) sekcji.  
  
<a name="implicit_conversion_with_the_implicit_operator"></a>   
## <a name="implicit-conversion-with-the-implicit-operator"></a>Niejawna konwersja za pomocą operatora Implicit  
 Konwersje rozszerzające obejmują utworzenie nowej wartości z wartości istniejącego typu, która ma bardziej ograniczony zakres lub bardziej ograniczoną listę elementów członkowskich niż typ docelowy. Konwersje rozszerzające nie mogą powodować utraty danych (chociaż mogą powodować utratę dokładności). Dane nie mogą być tracone, więc kompilatory mogą obsługiwać konwersję niejawnie (niewidocznie), dzięki czemu użytkownik nie musi używać jawnej metody konwersji ani operatora rzutowania.  
  
> [!NOTE]
>  Mimo że kod wywołujący niejawną konwersję może wywołać metodę konwersji lub użyć operatora rzutowania, ich użycie nie jest wymagane przez kompilatory obsługujące konwersje niejawne.  
  
 Na przykład <xref:System.Decimal> typu obsługuje niejawną konwersję z <xref:System.Byte>, <xref:System.Char>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.UInt16>, <xref:System.UInt32>, i <xref:System.UInt64> wartości. Poniższy przykład przedstawia niektóre z tych niejawne konwersje przypisywanie wartości do <xref:System.Decimal> zmiennej.  
  
 [!code-csharp[Conceptual.Conversion#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#1)]
 [!code-vb[Conceptual.Conversion#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#1)]  
  
 Jeśli kompilator określonego języka obsługuje operatory niestandardowe, niejawne konwersje można także definiować we własnych typach niestandardowych. W poniższym przykładzie przedstawiono częściowa implementacja bajtu ze znakiem typu danych o nazwie `ByteWithSign` używającą reprezentacja logowania i wielkości. Obsługuje ona niejawnej konwersji wartości <xref:System.Byte> i <xref:System.SByte> wartości do `ByteWithSign` wartości.  
  
 [!code-csharp[Conceptual.Conversion#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#2)]
 [!code-vb[Conceptual.Conversion#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#2)]  
  
 Następnie można zadeklarować kod klienta `ByteWithSign` zmiennej i przypisać je <xref:System.Byte> i <xref:System.SByte> wartości bez wykonywania jakiejkolwiek jawnej konwersji lub przy użyciu wszystkie operatory rzutowania, jak przedstawiono na poniższym przykładzie.  
  
 [!code-csharp[Conceptual.Conversion#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#3)]
 [!code-vb[Conceptual.Conversion#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#3)]  
  
 [Powrót do początku](#top)  
  
<a name="explicit_conversion_with_the_explicit_operator"></a>   
## <a name="explicit-conversion-with-the-explicit-operator"></a>Jawna konwersja za pomocą operatora Explicit  
 Konwersje zawężające obejmują utworzenie nowej wartości z wartości istniejącego typu, która ma większy zakres lub większą listę elementów członkowskich niż typ docelowy. Konwersja zawężająca może spowodować utratę danych, więc kompilatory często wymagają, aby taka konwersja została wykonana jawnie za pomocą wywołania metody konwersji lub operatora rzutowania. Oznacza to, że konwersja musi być jawnie obsługiwana w kodzie dewelopera.  
  
> [!NOTE]
>  Głównym celem wymagające metody konwersji lub operator rzutowania na zawężanie konwersji uświadomić dewelopera prawdopodobieństwo utraty danych lub <xref:System.OverflowException> , dzięki czemu mogą być obsługiwane w kodzie. Jednak niektóre kompilatory umożliwiają nieprzestrzeganie tego wymagania. Na przykład w Visual Basic, jeśli `Option Strict` jest wyłączone (ustawienie domyślne), próbuje wykonać niejawnej konwersji zawężającej kompilator Visual Basic.  
  
 Na przykład <xref:System.UInt32>, <xref:System.Int64>, i <xref:System.UInt64> typy danych mają zakresy, które przekraczają <xref:System.Int32> typu danych, jak to pokazano w poniższej tabeli.  
  
|Typ|Porównanie z zakresem typu Int32|  
|----------|------------------------------------|  
|<xref:System.Int64>|<xref:System.Int64.MaxValue?displayProperty=nameWithType>jest większa niż <xref:System.Int32.MaxValue?displayProperty=nameWithType>, i <xref:System.Int64.MinValue?displayProperty=nameWithType> jest mniejsza niż (większej liczby ujemne niż) <xref:System.Int32.MinValue?displayProperty=nameWithType>.|  
|<xref:System.UInt32>|<xref:System.UInt32.MaxValue?displayProperty=nameWithType>jest większa niż <xref:System.Int32.MaxValue?displayProperty=nameWithType>.|  
|<xref:System.UInt64>|<xref:System.UInt64.MaxValue?displayProperty=nameWithType>jest większa niż <xref:System.Int32.MaxValue?displayProperty=nameWithType>.|  
  
 Do obsługi takich konwersji zawężającej, [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] umożliwia typy, aby zdefiniować `Explicit` operatora. Kompilatory języka poszczególnych można następnie wdrożyć to rozwiązanie tego operatora za pomocą ich własnych składni lub członkiem <xref:System.Convert> klasy można wywołać w celu wykonania konwersji. (Aby uzyskać więcej informacji na temat <xref:System.Convert> , zobacz [klasy przekonwertować](#Convert) dalszej części tego tematu.) Poniższy przykład przedstawia użycie funkcje językowe jawną konwersję te wartości całkowite potencjalnie out-of-range, aby obsłużyć <xref:System.Int32> wartości.  
  
 [!code-csharp[Conceptual.Conversion#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#4)]
 [!code-vb[Conceptual.Conversion#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#4)]  
  
 Jawne konwersje może wygenerować różne wyniki w różnych językach, a wyniki te mogą się różnić od wartości zwróconej przez odpowiednie <xref:System.Convert> metody. Na przykład jeśli <xref:System.Double> wartość 12.63251 jest konwertowana na <xref:System.Int32>, zarówno Visual Basic `CInt` — metoda i .NET Framework <xref:System.Convert.ToInt32%28System.Double%29?displayProperty=nameWithType> round — metoda <xref:System.Double> ma zostać zwrócona wartość 13, ale C# `(int)` — operator obcina <xref:System.Double> ma zostać zwrócona wartość 12. Podobnie, C# `(int)` operator nie obsługuje konwersji typu Boolean do liczby całkowitej, ale Visual Basic `CInt` metoda konwertuje wartość `true` -1. Z drugiej strony <xref:System.Convert.ToInt32%28System.Boolean%29?displayProperty=nameWithType> metoda konwertuje wartość `true` do 1.  
  
 Większość kompilatorów zezwala na wykonywanie jawnych konwersji w sposób kontrolowany i niekontrolowany. Po wykonaniu konwersji zaznaczone <xref:System.OverflowException> jest generowany, gdy wartość typu do skonwertowania jest poza zakresem typu docelowego. Gdy w tych samych warunkach jest wykonywania konwersja niekontrolowana, konwersja może nie zgłosić wyjątku, ale dokładne zachowanie jest niezdefiniowane i może powstać niepoprawna wartość.  
  
> [!NOTE]
>  W języku C#, zaznaczone konwersji mogą być wykonywane przy użyciu `checked` — słowo kluczowe wraz z operatora rzutowania lub określając `/checked+` — opcja kompilatora. Z drugiej strony, konwersje zaznaczenie opcji można wykonać za pomocą `unchecked` — słowo kluczowe wraz z operatora rzutowania lub określając `/checked-` — opcja kompilatora. Domyślnie konwersje jawne są niekontrolowane. W języku Visual Basic zaznaczeniu tej opcji można wykonać konwersji czyszcząc **Wyłącz sprawdzanie przepełnienia całkowitych** pole wyboru w projekcie **Zaawansowane ustawienia kompilatora** okno dialogowe, lub określając `/removeintchecks-`— opcja kompilatora. Z drugiej strony, można wykonać konwersji niezaznaczone wybierając **Wyłącz sprawdzanie przepełnienia całkowitych** pole wyboru w projekcie **Zaawansowane ustawienia kompilatora** okno dialogowe lub określając `/removeintchecks+`— opcja kompilatora. Domyślnie konwersje jawne są kontrolowane.  
  
 W poniższym przykładzie C# `checked` i `unchecked` słów kluczowych w celu zilustrowania różnicy zachowania, gdy wartość spoza zakresu <xref:System.Byte> jest konwertowana na <xref:System.Byte>. Konwersja zaznaczone zgłasza wyjątek, ale przypisuje niezaznaczone konwersji <xref:System.Byte.MaxValue?displayProperty=nameWithType> do <xref:System.Byte> zmiennej.  
  
 [!code-csharp[Conceptual.Conversion#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#12)]  
  
 Jeśli kompilator danego języka obsługuje niestandardowe operatory przeciążone, konwersje jawne można także definiować we własnych typach niestandardowych. W poniższym przykładzie przedstawiono częściowa implementacja bajtu ze znakiem typu danych o nazwie `ByteWithSign` używającą reprezentacja logowania i wielkości. Obsługuje ona jawna konwersja <xref:System.Int32> i <xref:System.UInt32> wartości do `ByteWithSign` wartości.  
  
 [!code-csharp[Conceptual.Conversion#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#5)]
 [!code-vb[Conceptual.Conversion#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#5)]  
  
 Następnie można zadeklarować kod klienta `ByteWithSign` zmiennej i przypisz je <xref:System.Int32> i <xref:System.UInt32> wartości w przypadku przypisania obejmują operatora rzutowania lub konwersji metody, jak przedstawiono na poniższym przykładzie.  
  
 [!code-csharp[Conceptual.Conversion#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#6)]
 [!code-vb[Conceptual.Conversion#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#6)]  
  
 [Powrót do początku](#top)  
  
<a name="the_iconvertible_interface"></a>   
## <a name="the-iconvertible-interface"></a>Interfejs IConvertible  
 Do obsługi konwersji dowolnego typu do wspólnego języka środowiska uruchomieniowego typu podstawowego, [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] zapewnia <xref:System.IConvertible> interfejsu. Typ implementujący musi dostarczyć następujące elementy:  
  
-   Metoda, która zwraca <xref:System.TypeCode> typu implementującej.  
  
-   Typ metod do konwertowania implementujący do każdego wspólnego typu podstawowego środowiska uruchomieniowego języka (<xref:System.Boolean>, <xref:System.Byte>, <xref:System.DateTime>, <xref:System.Decimal>, <xref:System.Double>i tak dalej).  
  
-   Uogólnioną metodę konwersji służącą do konwertowania wystąpienia typu implementującego na inny określony typ. Konwersje, które nie są obsługiwane powinien zgłosić <xref:System.InvalidCastException>.  
  
 Każdy wspólnego typu podstawowego środowiska wykonawczego języka (to znaczy <xref:System.Boolean>, <xref:System.Byte>, <xref:System.Char>, <xref:System.DateTime>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.String>, <xref:System.UInt16>, <xref:System.UInt32>, i <xref:System.UInt64>), jak również <xref:System.DBNull> i <xref:System.Enum> typów wdrożenia <xref:System.IConvertible> interfejsu. Jednak te są jawne implementacje interfejsu; Metoda konwersji można wywołać tylko za pośrednictwem <xref:System.IConvertible> interfejsu zmiennej, jak przedstawiono na poniższym przykładzie. W tym przykładzie konwertuje <xref:System.Int32> wartości na jej odpowiednik <xref:System.Char> wartość.  
  
 [!code-csharp[Conceptual.Conversion#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible1.cs#7)]
 [!code-vb[Conceptual.Conversion#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible1.vb#7)]  
  
 Wymaganie, aby metoda konwersji była wywoływana w jej interfejsie, a nie w typie implementującym, powoduje, że jawne implementacje interfejsu są relatywnie kosztowne. Zalecany jest telefoniczne skontaktowanie się z odpowiednią członkiem <xref:System.Convert> klasy, które umożliwia konwersję pomiędzy popularne typy podstawowe środowisko uruchomieniowe języka. Aby uzyskać więcej informacji, zobacz następną sekcję, [przekonwertować klasy](#Convert).  
  
> [!NOTE]
>  Oprócz <xref:System.IConvertible> interfejsu i <xref:System.Convert> klasy przez [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], poszczególne języki może również udostępniać sposobów wykonywania konwersji. Na przykład C# używa operatorów rzutowania; Visual Basic używa funkcji konwersji implementowane przez kompilator takich jak `CType`, `CInt`, i `DirectCast`.  
  
 W większości przypadków <xref:System.IConvertible> interfejsu jest przeznaczony do obsługi konwersji między typami podstawowymi w [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Jednak ten interfejs może też być implementowany przez typ niestandardowy w celu obsługi konwersji tego typu na inny typ niestandardowy. Aby uzyskać więcej informacji, zobacz sekcję [niestandardowe konwersje z metodą ChangeType](#ChangeType) dalszej części tego tematu.  
  
 [Powrót do początku](#top)  
  
<a name="Convert"></a>   
## <a name="the-convert-class"></a>Klasa Convert  
 Mimo że każdy typ podstawowy <xref:System.IConvertible> implementacji interfejsu można wywołać, aby dokonać konwersji typu, wywoływanie metod <xref:System.Convert?displayProperty=nameWithType> klasy jest zalecany sposób niezależny od języka Aby przekonwertować z jednego typu podstawowego. Ponadto <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody można użyć do konwersji z określonego typu niestandardowego do innego typu.  
  
### <a name="conversions-between-base-types"></a>Konwersje między typami podstawowymi  
 <xref:System.Convert> Klasy udostępnia sposób niezależny od języka do wykonywania konwersji między typami podstawowej i jest dostępny dla wszystkich języków, których miejscem docelowym jest środowisko uruchomieniowe języka wspólnego. Zapewnia zarówno rozszerzanie i zwężanie konwersji kompletny zestaw metod i zgłasza <xref:System.InvalidCastException> podczas konwersji, które nie są obsługiwane (takich jak konwersji <xref:System.DateTime> wartość na wartość całkowitą). Konwersji zawężającej są wykonywane w kontekście zaznaczone, a <xref:System.OverflowException> jest generowany, jeśli konwersja nie powiedzie się.  
  
> [!IMPORTANT]
>  Ponieważ <xref:System.Convert> klasa zawiera metody do przekonwertowania do i z każdego typu podstawowego, eliminuje konieczność kontaktowania się każdego typu podstawowego <xref:System.IConvertible> jawnej implementacji interfejsu.  
  
 Poniższy przykład przedstawia użycie <xref:System.Convert?displayProperty=nameWithType> klasy do wykonania kilku rozszerzanie i zwężanie konwersji między typami podstawowej .NET Framework.  
  
 [!code-csharp[Conceptual.Conversion#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#8)]
 [!code-vb[Conceptual.Conversion#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#8)]  
  
 W niektórych przypadkach, zwłaszcza w przypadku konwertowania do i z wartości zmiennoprzecinkowych, konwersja może obejmować utratę dokładności, nawet jeśli nie zgłasza <xref:System.OverflowException>. W poniższym przykładzie pokazano taką utratę dokładności. W pierwszym przypadku <xref:System.Decimal> wartości jest mniejsza dokładność (mniejszą liczbę cyfr znaczących) po przekonwertowaniu do <xref:System.Double>. W drugim przypadku <xref:System.Double> wartość jest zaokrąglana z 42.72 do 43, aby można było ukończyć konwersję.  
  
 [!code-csharp[Conceptual.Conversion#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#9)]
 [!code-vb[Conceptual.Conversion#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#9)]  
  
 Dla tabeli, która zawiera zarówno rozszerzanie i zwężanie konwersji obsługiwane przez <xref:System.Convert> , zobacz [tabele konwersji typów](../../../docs/standard/base-types/conversion-tables.md).  
  
<a name="ChangeType"></a>   
### <a name="custom-conversions-with-the-changetype-method"></a>Konwersje niestandardowe z użyciem metody ChangeType  
 Oprócz obsługi konwersje do każdego z typów podstawowych <xref:System.Convert> klasa może być używana do przekonwertowania typu niestandardowego do co najmniej jeden wstępnie zdefiniowanych typów. Ta konwersja jest wykonywana przez <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metodę, która z kolei opakowuje wywołanie <xref:System.IConvertible.ToType%2A?displayProperty=nameWithType> metody `value` parametru. Oznacza to, że obiekt reprezentowany przez `value` parametru musi zapewniać implementację elementu <xref:System.IConvertible> interfejsu.  
  
> [!NOTE]
>  Ponieważ <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%29?displayProperty=nameWithType> i <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody <xref:System.Type> obiekt, aby określić typ obiektu docelowego, do którego `value` jest konwersji one można dokonać konwersji dynamicznych do obiektu, którego typ jest nieznany w czasie kompilacji. Jednak należy pamiętać, że <xref:System.IConvertible> implementacja `value` nadal musi obsługiwać tę konwersję.  
  
 Poniższy przykład przedstawia możliwości stosowania <xref:System.IConvertible> interfejs, umożliwiający `TemperatureCelsius` obiekt ma zostać przekonwertowane na `TemperatureFahrenheit` obiektu i na odwrót. W przykładzie zdefiniowano klasę podstawową `Temperature`, który implementuje <xref:System.IConvertible> interfejsu i zastąpień <xref:System.Object.ToString%2A?displayProperty=nameWithType> — metoda. Pochodne `TemperatureCelsius` i `TemperatureFahrenheit` klasy każdego zastąpienie `ToType` i `ToString` metody klasy podstawowej.  
  
 [!code-csharp[Conceptual.Conversion#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#10)]
 [!code-vb[Conceptual.Conversion#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#10)]  
  
 Poniższy przykład przedstawia kilka tych wywołań <xref:System.IConvertible> implementacji, aby przekonwertować `TemperatureCelsius` obiekty do `TemperatureFahrenheit` obiektów i na odwrót.  
  
 [!code-csharp[Conceptual.Conversion#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#11)]
 [!code-vb[Conceptual.Conversion#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#11)]  
  
 [Powrót do początku](#top)  
  
<a name="the_typeconverter_class"></a>   
## <a name="the-typeconverter-class"></a>Klasa TypeConverter  
 .NET Framework można również zdefiniować konwerter typu dla typu niestandardowego rozszerzając <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType> klasy i kojarzenie z typem za pomocą konwertera typu <xref:System.ComponentModel.TypeConverterAttribute?displayProperty=nameWithType> atrybutu. W poniższej tabeli wymieniono różnice między tą metodą i wdrażanie <xref:System.IConvertible> interfejs dla typu niestandardowego.  
  
> [!NOTE]
>  Obsługa typu niestandardowego w czasie projektowania jest możliwa tylko wtedy, gdy zdefiniowano dla niego konwerter typów.  
  
|Konwersja z użyciem klasy TypeConverter|Konwersja z użyciem interfejsu IConvertible|  
|------------------------------------|-----------------------------------|  
|Zaimplementowano dla niestandardowego typu pochodnego osobnej klasy z <xref:System.ComponentModel.TypeConverter>. Ta klasa pochodna jest skojarzony z typu niestandardowego, stosując <xref:System.ComponentModel.TypeConverterAttribute> atrybutu.|Jest implementowana przez typ niestandardowy w celu wykonania konwersji. Użytkownik typu wywołuje <xref:System.IConvertible> metody konwersji typu.|  
|Może być używana w czasie projektowania i w czasie wykonywania.|Może być używana tylko w czasie wykonywania.|  
|Używa odbicia; w związku z tym jest mniejsza niż konwersji włączane przez <xref:System.IConvertible>.|Nie używa odbicia.|  
|Umożliwia dwukierunkowe konwersje typów z typu niestandardowego na inne typy danych i z innych typów danych na typ niestandardowy. Na przykład <xref:System.ComponentModel.TypeConverter> zdefiniowane dla `MyType` umożliwia konwersję z `MyType` do <xref:System.String>i z <xref:System.String> do `MyType`.|Umożliwia konwersję z typu niestandardowego na inne typy danych, ale nie z innych typów danych na typ niestandardowy.|  
  
 Aby uzyskać więcej informacji o używaniu konwertery typu do wykonywania konwersji, zobacz <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Convert?displayProperty=nameWithType>  
 <xref:System.IConvertible>  
 [Tabele konwersji typów](../../../docs/standard/base-types/conversion-tables.md)
