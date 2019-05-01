---
title: Podstawy zabezpieczeń dostępu kodu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], code access security
ms.assetid: 4eaa6535-d9fe-41a1-91d8-b437cfc16921
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8d5a5658fcb6bbba72938a16a9e5c82fd779e2e3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61868774"
---
# <a name="code-access-security-basics"></a>Podstawy zabezpieczeń dostępu kodu

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Każda aplikacja, który jest przeznaczony dla środowiska uruchomieniowego języka wspólnego (tzn. Każda zarządzana aplikacja) musi współdziałać z systemu zabezpieczeń w środowisku uruchomieniowym. Po załadowaniu aplikacji zarządzanej, jej hosta automatycznie udziela on zestaw uprawnień. Te uprawnienia są określane przez ustawienia zabezpieczeń lokalnych hosta lub piaskownicy, w której znajduje się aplikacja. W zależności od tych uprawnień aplikacja działa prawidłowo lub generuje wyjątek zabezpieczeń.

Domyślny host dla aplikacji klasycznych umożliwia uruchamianie kodu w trybie pełnego zaufania. W związku z tym, czy aplikacja jest przeznaczona na pulpicie, ma on nieograniczonych uprawnień zestawu. Innych hostów lub w piaskownicach należy zapewnić ograniczone uprawnienia ustawione dla aplikacji. Ponieważ zestaw uprawnień mogą ulec zmianie między hostami, należy zaprojektować aplikację, aby korzystać z uprawnień, które zezwala na dostęp do hosta docelowego.

Należy zapoznać się z następujących koncepcji zabezpieczeń dostępu kodu w celu pisania aplikacji, od obiektu docelowego środowiska uruchomieniowego języka wspólnego:

- **Kod bezpiecznego typu**: Kod bezpiecznego typu jest kod, który uzyskuje dostęp do typów wyłącznie na wyraźnie określone, dozwolone sposoby. Na przykład, biorąc pod uwagę odwołania prawidłowego obiektu, bezpieczny kod może uzyskać dostęp pamięci na stałych przesunięcia, które odnoszą się do elementów członkowskich pola rzeczywistej. Jeśli kod uzyskuje dostęp do pamięci dowolnego przesunięcia poza zakres pamięci, który należy do tego obiektu publicznie widoczne pola, nie jest bezpieczny. Aby włączyć kod, aby korzystać z zabezpieczeń dostępu kodu, należy użyć kompilatora, które generuje sprawdzalnie bezpieczny kod. Aby uzyskać więcej informacji, zobacz [pisania Sprawdzalnie bezpieczny kod](#typesafe_code) w dalszej części tego tematu.

- **Składnia imperatywną lub deklaratywną**: Kod ten obiektów docelowych, które środowisko uruchomieniowe języka wspólnego może współdziałać z system zabezpieczeń, za pomocą żądania uprawnień, wymagających, że obiekty wywołujące określony uprawnienia i przesłanianie niektórych ustawień zabezpieczeń (podane wystarczających uprawnień). Użycie dwóch metod składni, aby programowo współdziałać z system zabezpieczeń .NET Framework: składni deklaratywnej i składnia imperatywna. Deklaratywne wywołania są wykonywane przy użyciu atrybutów, a imperatywne wywołania są wykonywane przy użyciu nowych wystąpień klasy w kodzie. Niektóre połączenia, które mogą być wykonywane tylko obowiązkowo, inne osoby mogą być wykonywane tylko w sposób deklaratywny i niektóre połączenia mogą być wykonywane w sposób, w obu.

- **Zabezpieczanie bibliotek klas**: Biblioteki klas bezpiecznego używa wymogów bezpieczeństwa, aby upewnić się, że obiekty wywołujące w bibliotece programu mają uprawnienia dostępu do zasobów, które udostępnia biblioteki. Na przykład biblioteki klas bezpiecznego może być metodą tworzenia plików wymagających spowoduje, że elementy go wywołujące pod mają uprawnienia do tworzenia plików. .NET Framework składa się z zabezpieczonych bibliotek klas. Należy pamiętać o uprawnienia wymagane do uzyskania dostępu wszystkie biblioteki, która korzysta z kodu. Aby uzyskać więcej informacji, zobacz [przy użyciu biblioteki klas Secure](#secure_library) w dalszej części tego tematu.

- **Kod o przezroczystym**: Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], oprócz identyfikowania określonych uprawnień, należy także określić czy kodzie powinno być uruchomione jako zabezpieczenia przejrzysty. Kod o przezroczystym poziomie bezpieczeństwa nie można wywołać typy lub elementy członkowskie, które są identyfikowane jako krytyczne dla bezpieczeństwa. Ta reguła ma zastosowanie do aplikacji pełnego zaufania, a także częściowo zaufanych aplikacji. Aby uzyskać więcej informacji, zobacz [kod o przezroczystym poziomie bezpieczeństwa](../../../docs/framework/misc/security-transparent-code.md).

<a name="typesafe_code"></a>

## <a name="writing-verifiably-type-safe-code"></a>Sprawdzalnie bezpieczny kod

Just-in-time (JIT) kompilacja wykonuje proces weryfikacji, który sprawdza kod i próbuje określić, czy kod jest bezpieczny. Jest wywoływana przez kod, który jest sprawdzana podczas weryfikacji jako bezpieczny *sprawdzalnie bezpieczny kod*. Kod może być bezpieczne, jeszcze może nie być sprawdzalnie bezpieczny ze względu na ograniczenia procesu weryfikacji lub kompilatora. Nie wszystkie języki są bezpieczne, a niektóre Kompilatory języka, takich jak Microsoft Visual C++ nie można wygenerować sprawdzalnie bezpieczny kod zarządzany. Aby ustalić, czy kompilator języka, którego używasz generuje sprawdzalnie bezpieczny kod, zapoznaj się z dokumentacją kompilatora. Jeśli używasz kompilator języka, który generuje sprawdzalnie bezpieczny kod, tylko wtedy, gdy można uniknąć pewnych konstrukcji języka, możesz chcieć użyć [narzędzie PEVerify](../../../docs/framework/tools/peverify-exe-peverify-tool.md) do ustalenia, czy kod jest sprawdzalnie bezpieczny.

Kod, który nie jest sprawdzalnie bezpieczny, można spróbować wykonać, jeśli kod, aby pominąć weryfikację pozwalają zasady zabezpieczeń. Jednak ponieważ bezpieczeństwo typów jest integralną część mechanizm izolowanie zestawy w środowisku uruchomieniowym, zabezpieczeń nie można niezawodnie wymusić Jeśli kod narusza zasady zabezpieczeń. Domyślnie kod, który nie jest bezpieczny można uruchamiać tylko wtedy, gdy pochodzi z komputera lokalnego. Dlatego kod przenośny powinny być bezpieczne.

<a name="secure_library"></a>

## <a name="using-secure-class-libraries"></a>Przy użyciu zabezpieczonych bibliotek klas

Jeśli Twój kod żądań i jest przyznano uprawnienia wymagane przez bibliotekę klas, może być na dostęp do biblioteki i zasobów, które udostępnia biblioteki będą chronione przed nieautoryzowanym dostępem. Jeśli kod nie ma odpowiednich uprawnień, go nie będzie można na dostęp do biblioteki klas, a złośliwy kod nie będzie można użyć kodu pośrednio uzyskać dostęp do chronionych zasobów. Inny kod, który wywołuje kod również musi mieć uprawnienia do dostępu do biblioteki. Jeśli nie, Twój kod będzie dotyczyć wymaga również.

Zabezpieczenia dostępu kodu nie eliminuje możliwości ludzkiego błędu w pisaniu kodu. Jednak jeśli Twoja aplikacja używa zabezpieczonych bibliotek klas dostępu do zasobów chronionych, zagrożenie bezpieczeństwa, aby kod aplikacji zmniejsza się, ponieważ biblioteki klas są ściśle kontroli dla potencjalnych problemów z zabezpieczeniami.

## <a name="declarative-security"></a>Zabezpieczenia deklaratywne

Składnia zabezpieczeń deklaratywnych używa [atrybuty](../../../docs/standard/attributes/index.md) można umieścić informacje o zabezpieczeniach do [metadanych](../../../docs/standard/metadata-and-self-describing-components.md) kodu. Atrybuty mogą być umieszczone na poziomie zestawu, klasy lub elementu członkowskiego, aby wskazać typ żądania, żądanie lub zastąpienie, którego chcesz użyć. Żądania są używane w aplikacjach przeznaczonych dla środowiska uruchomieniowego języka wspólnego poinformować system zabezpieczeń środowiska wykonawczego o uprawnienia, które aplikacja potrzebuje lub nie ma. Wymagania i zastąpienia są używane w bibliotekach, w celu ochrony zasobów obiektów wywołujących lub aby zastąpić domyślne zachowanie zabezpieczeń.

> [!NOTE]
> W [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], miały miejsce istotne zmiany w modelu zabezpieczeń .NET Framework i terminologię. Aby uzyskać więcej informacji o tych zmianach, zobacz [zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md).

Aby można było używać zabezpieczeń deklaracyjnych wywołań, musisz zainicjować dane o stanie obiektu uprawnienia tak, aby reprezentuje danego formularza uprawnień, których potrzebujesz. Wszystkie wbudowane uprawnienia ma atrybut, który jest przekazywany <xref:System.Security.Permissions.SecurityAction> wyliczenie opisujący typ operacji zabezpieczeń, którą chcesz wykonać. Uprawnienia zaakceptować również własne parametry, które są na wyłączność dla nich.

Poniższy fragment kodu przedstawia składni deklaratywnej do żądania, że obiekty wywołujące kodu mają niestandardowe uprawnienie o nazwie `MyPermission`. To uprawnienie jest hipotetyczny niestandardowe uprawnienie i nie istnieje w programie .NET Framework. W tym przykładzie wywołanie deklaratywne znajduje się bezpośrednio przed definicją klasy, określając, że to uprawnienie można zastosować do poziomu klasa. Ten atrybut jest przekazywany **SecurityAction.Demand** struktury, aby określić, że obiekty wywołujące muszą mieć to uprawnienie, aby można było uruchomić.

```vb
<MyPermission(SecurityAction.Demand, Unrestricted = True)> Public Class MyClass1

   Public Sub New()
      'The constructor is protected by the security call.
   End Sub

   Public Sub MyMethod()
      'This method is protected by the security call.
   End Sub

   Public Sub YourMethod()
      'This method is protected by the security call.
   End Sub
End Class
```

```csharp
[MyPermission(SecurityAction.Demand, Unrestricted = true)]
public class MyClass
{
   public MyClass()
   {
      //The constructor is protected by the security call.
   }

   public void MyMethod()
   {
      //This method is protected by the security call.
   }

   public void YourMethod()
   {
      //This method is protected by the security call.
   }
}
```

## <a name="imperative-security"></a>Zabezpieczenia imperatywne

Składnia zabezpieczeń imperatywnych generuje wywołanie zabezpieczeń, tworząc nowe wystąpienie obiektu uprawnień, który chcesz wywołać. Składnia imperatywna służy do wykonania żądania i zastąpienia, ale nie żądań.

Przed wprowadzeniem zabezpieczeń wywołania dane o stanie obiektu uprawnienia musi zostać zainicjowany, aby reprezentuje danego formularza uprawnień, których potrzebujesz. Na przykład podczas tworzenia <xref:System.Security.Permissions.FileIOPermission> obiektu, aby zainicjować można użyć konstruktora **FileIOPermission** obiekt reprezentuje albo nieograniczony dostęp do wszystkich plików lub Brak dostępu do plików. Alternatywnie można użyć innego **FileIOPermission** obiektu, przekazanie parametrów, które wskazują na typ ma dostęp do obiektu reprezentują (oznacza to, odczytu, Dołącz lub zapis) i które pliki mają obiektu do ochrony.

Oprócz używania składnia zabezpieczeń imperatywnych do obiektu zabezpieczeń pojedynczego wywołania, można użyć go zainicjować grupy uprawnień w zestawie uprawnień. Na przykład ta technika jest jedynym sposobem niezawodnie wykonać [asercja](../../../docs/framework/misc/using-the-assert-method.md) wywołuje wiele uprawnień w jednej metody. Użyj <xref:System.Security.PermissionSet> i <xref:System.Security.NamedPermissionSet> klasy, aby utworzyć grupy uprawnień, a następnie wywołać odpowiedniej metody do wywołania wywołania pożądanych zabezpieczeń.

Składnia imperatywna służy do wykonania żądania i zastąpienia, ale nie żądań. Może na użytek składnia imperatywna wymagań i zastępuje zamiast składni deklaratywnej, jeśli informacje potrzebne, aby zainicjować stan uprawnień staje się znane tylko w czasie wykonywania. Na przykład jeśli chcesz upewnić się, że obiekty wywołujące ma uprawnienia do odczytu określonego pliku, ale nie znasz nazwę tego pliku do czasu wykonywania, należy użyć imperatywne żądanie. Można także do użycia imperatywne sprawdzanie zamiast deklaratywne sprawdzanie gdy zachodzi potrzeba określenia w czasie wykonywania, czy zawiera warunek i, na podstawie wyniku testu, żądanie zabezpieczeń (lub nie).

Poniższy fragment kodu przedstawia składnia imperatywna do żądania, że obiekty wywołujące kodu mają niestandardowe uprawnienie o nazwie `MyPermission`. To uprawnienie jest hipotetyczny niestandardowe uprawnienie i nie istnieje w programie .NET Framework. Nowe wystąpienie klasy `MyPermission` jest tworzony w `MyMethod`, ochrona tylko tej metody za pomocą wywołania zabezpieczeń.

```vb
Public Class MyClass1

   Public Sub New()

   End Sub

   Public Sub MyMethod()
      'MyPermission is demanded using imperative syntax.
      Dim Perm As New MyPermission()
      Perm.Demand()
      'This method is protected by the security call.
   End Sub

   Public Sub YourMethod()
      'YourMethod 'This method is not protected by the security call.
   End Sub
End Class
```

```csharp
public class MyClass {
   public MyClass(){

   }

   public void MyMethod() {
       //MyPermission is demanded using imperative syntax.
       MyPermission Perm = new MyPermission();
       Perm.Demand();
       //This method is protected by the security call.
   }

   public void YourMethod() {
       //This method is not protected by the security call.
   }
}
```

## <a name="using-managed-wrapper-classes"></a>Używanie zarządzanych klas otoki

Większość aplikacji i składników (z wyjątkiem bezpiecznych bibliotek) nie należy bezpośrednio wywoływać kod niezarządzany. Istnieje kilka przyczyn. Jeśli kod wywołuje kod niezarządzany bezpośrednio, nie będą mogą działać w wielu sytuacjach, ponieważ należy udzielić kodowi wysokiego poziomu zaufania, aby wywołać kodu natywnego. W przypadku modyfikowania zasad umożliwiających aplikacji do uruchomienia go znacząco obniżyć poziom zabezpieczeń systemu, pozostawiając ją do wykonywania niemal wszystkich operacji.

Ponadto kod, który ma uprawnienia do dostępu do kodu niezarządzanego prawdopodobnie operację mogą wykonać prawie każdym za pośrednictwem wywołania do niezarządzanego interfejsu API. Na przykład, kod, który ma uprawnienia do wywoływania niezarządzanego kodu nie jest konieczne <xref:System.Security.Permissions.FileIOPermission> dostępu do pliku; może wywołać tylko niezarządzane (Win32) interfejsu API plików bezpośrednio, pomijanie pliku zarządzanego interfejsu API, który wymaga **FileIOPermission**. Jeśli kod zarządzany ma uprawnienia do wywołania kodu niezarządzanego i wywołać bezpośrednio do kodu niezarządzanego, system zabezpieczeń będzie mógł niezawodne wymuszania ograniczeń zabezpieczeń, ponieważ środowisko uruchomieniowe nie może wymusić takie ograniczenia dotyczące kodu niezarządzanego.

Chcąc aplikacji do wykonywania operacji, która wymaga dostępu do kodu niezarządzanego, go należy to zrobić za pomocą zaufanego klasy zarządzanej, która otacza funkcjonalność wymagane (jeśli istnieje taka klasa). Nie należy tworzyć klasy otoki samodzielnie, jeśli istnieje już w bibliotece bezpiecznych klasy. Klasa otoki, które muszą być przyznane wysoki stopień zaufania, aby mieć możliwość wykonania wywołania kodu niezarządzanego, jest odpowiedzialny za wymagających, że elementy go wywołujące pod mają odpowiednie uprawnienia. Jeśli używasz klasy otoki, kod musi tylko żądania i mieć przyznane uprawnienia, które wymaga klasy otoki.

## <a name="see-also"></a>Zobacz także

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.NamedPermissionSet>
- <xref:System.Security.Permissions.SecurityAction>
- [Assert](../../../docs/framework/misc/using-the-assert-method.md)
- [Zabezpieczenia dostępu kodu](../../../docs/framework/misc/code-access-security.md)
- [Podstawy zabezpieczeń dostępu kodu](../../../docs/framework/misc/code-access-security-basics.md)
- [Atrybuty](../../../docs/standard/attributes/index.md)
- [Składniki samoopisujące się i metadane](../../../docs/standard/metadata-and-self-describing-components.md)
