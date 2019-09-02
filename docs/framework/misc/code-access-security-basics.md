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
ms.openlocfilehash: d77683dde24eeec5de7f1e541a6cc86f3b0c6617
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205633"
---
# <a name="code-access-security-basics"></a>Podstawy zabezpieczeń dostępu kodu

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Każda aplikacja, która jest przeznaczona dla środowiska uruchomieniowego języka wspólnego (czyli każda zarządzana aplikacja) musi współdziałać z systemem zabezpieczeń środowiska uruchomieniowego. Gdy zarządzana aplikacja jest ładowana, jej Host automatycznie przyznaje jej zestaw uprawnień. Te uprawnienia są określane przez ustawienia zabezpieczeń lokalnych hosta lub piaskownicy, w których znajduje się aplikacja. W zależności od tych uprawnień aplikacja działa prawidłowo lub generuje wyjątek zabezpieczeń.

Domyślny Host dla aplikacji klasycznych umożliwia uruchamianie kodu w trybie pełnego zaufania. W związku z tym, jeśli aplikacja jest przeznaczona dla pulpitu, ma nieograniczony zestaw uprawnień. Inne hosty i piaskownicy zapewniają ograniczone zestawy uprawnień dla aplikacji. Ze względu na to, że zestaw uprawnień może się zmienić z hosta na host, należy zaprojektować aplikację tak, aby korzystała tylko z uprawnień, które zezwala hostowi docelowemu.

Aby pisać efektywne aplikacje przeznaczone dla środowiska uruchomieniowego języka wspólnego, należy zapoznać się z poniższymi pojęciami dotyczącymi zabezpieczeń.

- **Kod bezpieczny dla typu**: Kod bezpieczny dla typów to kod, który uzyskuje dostęp do typów tylko w dobrze zdefiniowanych, dozwolonych sposobach. Na przykład, uwzględniając prawidłowy odwołanie do obiektu, kod bezpieczny dla typu może uzyskać dostęp do pamięci przy stałych przesunięciach, które odpowiadają rzeczywistym elementom członkowskim pola. Jeśli kod uzyskuje dostęp do pamięci w dowolnym przesunięciu poza zakresem pamięci, który należy do pól publicznie narażonych obiektów, nie jest bezpieczny dla typów. Aby umożliwić programowi Code korzystanie z zabezpieczeń dostępu kodu, należy użyć kompilatora, który generuje kod bezpieczny dla typów. Aby uzyskać więcej informacji, zobacz sekcję [pisanie kodu z bezpiecznym typem](#typesafe_code) w dalszej części tego tematu.

- Składnia bezwzględna **i deklaracyjne**: Kod, który jest przeznaczony dla środowiska uruchomieniowego języka wspólnego, może współdziałać z systemem zabezpieczeń, żądając uprawnień, wymagających, aby wywołujący mieli określone uprawnienia, i zastępowaniem określonych ustawień zabezpieczeń (z uwzględnieniem wystarczających uprawnień). Używasz dwóch form składni, aby programowo korzystać z systemu zabezpieczeń .NET Framework: składni deklaratywnej i bezwzględnej składni. Wywołania deklaracyjne są wykonywane przy użyciu atrybutów; wywołania bezwzględne są wykonywane przy użyciu nowych wystąpień klas w kodzie. Niektóre wywołania mogą być wykonywane tylko bezterminowo, inne mogą być wykonywane tylko w sposób deklaratywny, a niektóre wywołania można wykonać w dowolny sposób.

- **Bezpieczne biblioteki klas**: Bezpieczna Biblioteka klas używa wymagań zabezpieczeń, aby upewnić się, że obiekty wywołujące biblioteki mają uprawnienia dostępu do zasobów udostępnianych przez bibliotekę. Na przykład biblioteka zabezpieczonych klas może mieć metodę tworzenia plików, które będą miały uprawnienia do tworzenia plików. .NET Framework składa się z zabezpieczonych bibliotek klas. Należy pamiętać o uprawnieniach wymaganych do uzyskania dostępu do dowolnej biblioteki używanej przez kod. Aby uzyskać więcej informacji, zobacz sekcję [using Secure Class](#secure_library) librarys w dalszej części tego tematu.

- **Kod przezroczysty**: Począwszy od .NET Framework 4, Oprócz określenia określonych uprawnień, należy również określić, czy kod powinien działać jako przezroczysty dla bezpieczeństwa. Kod przezroczysty pod względem zabezpieczeń nie może wywoływać typów lub elementów członkowskich, które są zidentyfikowane jako krytyczne dla zabezpieczeń. Ta reguła ma zastosowanie do aplikacji pełnego zaufania, a także częściowo zaufanych aplikacji. Aby uzyskać więcej informacji, zobacz [kod przezroczysty dla zabezpieczeń](security-transparent-code.md).

<a name="typesafe_code"></a>

## <a name="writing-verifiably-type-safe-code"></a>Pisanie kodu z bezpiecznym typem

Kompilacja just-in-Time (JIT) wykonuje proces weryfikacji, który sprawdza kod i próbuje określić, czy kod jest bezpieczny dla typów. Kod, który jest sprawdzony podczas weryfikacji, jest nazywany "możliwym do *sprawdzenia kodem bezpiecznym typem"* . Kod może być bezpieczny dla typów, ale nie można go sprawdzać bezpiecznie ze względu na ograniczenia procesu weryfikacji lub kompilatora. Nie wszystkie języki są bezpieczne dla typów, a niektóre kompilatory języka, takie jak Microsoft Visual C++, nie mogą generować z bezpiecznym typem kodu zarządzanego. Aby określić, czy używany kompilator języka generuje kod bezpieczny dla typu, należy zapoznać się z dokumentacją kompilatora. Jeśli używasz kompilatora języka, który generuje kod bezpieczny z typem możliwym do sprawdzenia tylko w przypadku uniknięcia niektórych konstrukcji językowych, możesz chcieć użyć [Narzędzia PEVerify](../tools/peverify-exe-peverify-tool.md) , aby określić, czy kod jest bezpieczny pod względem typów.

Kod, który nie jest możliwy do zweryfikowania typu, może podjąć próbę wykonania, jeśli zasady zabezpieczeń umożliwiają kod, aby obejść weryfikację. Jednak ze względu na to, że bezpieczeństwo typu jest istotną częścią mechanizmu środowiska uruchomieniowego dla izolowanych zestawów, zabezpieczenia nie mogą być niezawodne, jeśli kod narusza reguły bezpieczeństwa typu. Domyślnie kod, który nie jest bezpieczny pod względem typu, może być uruchamiany tylko wtedy, gdy pochodzi z komputera lokalnego. W związku z tym kod mobilny powinien być bezpieczny dla typów.

<a name="secure_library"></a>

## <a name="using-secure-class-libraries"></a>Korzystanie z bezpiecznych bibliotek klas

Jeśli kod zażąda uprawnień wymaganych przez bibliotekę klas, będzie można uzyskać dostęp do biblioteki, a zasoby uwidaczniane przez bibliotekę będą chronione przed nieautoryzowanym dostępem. Jeśli Twój kod nie ma odpowiednich uprawnień, nie będzie on mógł uzyskać dostępu do biblioteki klas, a złośliwy kod nie będzie mógł użyć kodu do pośredniego dostępu do chronionych zasobów. Inny kod, który wywołuje kod, musi mieć również uprawnienia dostępu do biblioteki. Jeśli tak nie jest, kod będzie ograniczony tylko do działania.

Zabezpieczenia dostępu kodu nie eliminują możliwości błędu ludzkiego podczas pisania kodu. Jeśli jednak aplikacja używa zabezpieczonych bibliotek klas w celu uzyskania dostępu do chronionych zasobów, zmniejsza się zagrożenie bezpieczeństwa związane z kodem aplikacji, ponieważ biblioteki klas są ściśle scrutinized w przypadku potencjalnych problemów z zabezpieczeniami.

## <a name="declarative-security"></a>Zabezpieczenia deklaratywne

Składnia zabezpieczeń deklaracyjnej używa [atrybutów](../../standard/attributes/index.md) do umieszczania informacji o zabezpieczeniach w [metadanych](../../standard/metadata-and-self-describing-components.md) kodu. Atrybuty mogą być umieszczane na poziomie zestawu, klasy lub elementu członkowskiego, aby wskazać typ żądania, żądanie lub przesłonięcie, którego chcesz użyć. Żądania są używane w aplikacjach przeznaczonych dla środowiska uruchomieniowego języka wspólnego, aby poinformować system zabezpieczeń środowiska uruchomieniowego o uprawnieniach wymaganych przez aplikację lub których nie ma. Wymagania i zastąpienia są używane w bibliotekach, aby ułatwić ochronę zasobów przed wywołującymi lub przesłaniać domyślne zachowanie zabezpieczeń.

> [!NOTE]
> W .NET Framework 4 wprowadzono ważne zmiany w modelu zabezpieczeń .NET Framework i terminologii. Aby uzyskać więcej informacji o tych zmianach, zobacz [zmiany zabezpieczeń](../security/security-changes.md).

Aby można było używać deklaratywnych wywołań zabezpieczeń, należy zainicjować dane stanu obiektu uprawnienia, aby reprezentować określoną formę odpowiedniego uprawnienia. Każde wbudowane uprawnienie ma atrybut, który <xref:System.Security.Permissions.SecurityAction> przekazuje Wyliczenie, aby opisać typ operacji zabezpieczeń, którą chcesz wykonać. Jednak uprawnienia akceptują także własne parametry, które są na wyłączność.

Poniższy fragment kodu przedstawia składnię deklaratywną dla żądania, że obiekt wywołujący kodu ma uprawnienie niestandardowe o nazwie `MyPermission`. To uprawnienie jest hipotetycznym uprawnieniem niestandardowym i nie istnieje w .NET Framework. W tym przykładzie wywołanie deklaracyjne jest umieszczane bezpośrednio przed definicją klasy, określając, że to uprawnienie jest stosowane do poziomu klasy. Ten atrybut jest przekazywać strukturę **SecurityAction. Demand** , aby określić, że wywołujący muszą mieć to uprawnienie, aby można było je uruchomić.

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

Bezwzględna składnia zabezpieczeń emituje wywołanie zabezpieczeń, tworząc nowe wystąpienie obiektu uprawnień, który ma zostać wywołany. Można użyć bezwzględnej składni, aby wykonać wymagania i zastąpienia, ale nie żądania.

Przed przystąpieniem do wywołania zabezpieczeń należy zainicjować dane stanu obiektu uprawnienia, aby reprezentować określoną formę odpowiedniego uprawnienia. Na przykład podczas tworzenia <xref:System.Security.Permissions.FileIOPermission> obiektu można użyć konstruktora, aby zainicjować obiekt **FileIOPermission** , aby reprezentować nieograniczony dostęp do wszystkich plików lub bez dostępu do plików. Można też użyć innego obiektu **FileIOPermission** , przekazując parametry wskazujące typ dostępu, który ma być reprezentowany przez obiekt (czyli odczyt, dołączenie lub zapis) i pliki, które mają być chronione przez obiekt.

Oprócz użycia bezwzględnej składni zabezpieczeń do wywołania pojedynczego obiektu zabezpieczeń można użyć go do zainicjowania grupy uprawnień w zestawie uprawnień. Na przykład ta technika jest jedynym sposobem nieniezawodnego wykonywania wywołań [potwierdzenia](using-the-assert-method.md) dla wielu uprawnień w jednej metodzie. Użyj klas <xref:System.Security.NamedPermissionSet> i, aby utworzyć grupę uprawnień, a następnie Wywołaj odpowiednią metodę w celu wywołania żądanego wywołania zabezpieczeń. <xref:System.Security.PermissionSet>

Można użyć bezwzględnej składni, aby wykonać wymagania i zastąpienia, ale nie żądania. Można użyć bezwzględnej składni dla wymagań i zastąpień zamiast składni deklaracyjnej, gdy informacje potrzebne do zainicjowania stanu uprawnień są znane tylko w czasie wykonywania. Na przykład jeśli chcesz mieć pewność, że obiekty wywołujące mają uprawnienia do odczytu określonego pliku, ale nie znasz nazwy tego pliku do czasu uruchomienia, użyj bezwzględnego zapotrzebowania. Można również użyć bezwzględnych kontroli zamiast kontroli deklaracyjnej, gdy zachodzi potrzeba określenia w czasie wykonywania, czy warunek zawiera i, na podstawie wyniku testu, nawiązać żądanie zabezpieczeń (lub nie).

Poniższy fragment kodu przedstawia niezbędną składnię do żądania, że obiekt wywołujący kodu ma uprawnienie niestandardowe o `MyPermission`nazwie. To uprawnienie jest hipotetycznym uprawnieniem niestandardowym i nie istnieje w .NET Framework. Nowe wystąpienie `MyPermission` jest tworzone w programie `MyMethod`, chroniąc tylko tę metodę za pomocą wywołania zabezpieczeń.

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

Większość aplikacji i składników (z wyjątkiem bezpiecznych bibliotek) nie powinna bezpośrednio wywołać kodu niezarządzanego. Istnieje kilka przyczyn tego. Jeśli kod niezarządzany jest bezpośrednio wywoływany, nie będzie można go uruchamiać w wielu przypadkach, ponieważ kod musi mieć przydzielony wysoki poziom zaufania, aby wywołać kod natywny. Jeśli zasady są modyfikowane w celu zezwolenia na uruchomienie takiej aplikacji, może znacząco obniżyć poziom bezpieczeństwa systemu, pozostawiając aplikację bezpłatnie do wykonania niemal każdej operacji.

Ponadto kod, który ma uprawnienia dostępu do niezarządzanego kodu, prawdopodobnie wykonuje niemal wszystkie operacje, wywołując do niezarządzanego interfejsu API. Na przykład kod, który ma uprawnienia do wywoływania niezarządzanego kodu, <xref:System.Security.Permissions.FileIOPermission> nie musi uzyskiwać dostępu do pliku. może tylko wywołać interfejs API plików niezarządzanych (Win32) bezpośrednio, pomijając interfejs API pliku zarządzanego, który wymaga **FileIOPermission**. Jeśli kod zarządzany ma uprawnienia do wywoływania kodu niezarządzanego i wywołuje bezpośrednio w kodzie niezarządzanym, system zabezpieczeń nie będzie w stanie niezawodnie wymuszać ograniczeń zabezpieczeń, ponieważ środowisko wykonawcze nie może wymusić takich ograniczeń dla niezarządzanego kodu.

Jeśli chcesz, aby aplikacja wykonywała operację wymagającą dostępu do kodu niezarządzanego, należy to zrobić za pomocą zaufanej klasy zarządzanej, która otacza wymagane funkcje (jeśli taka Klasa istnieje). Nie należy tworzyć klasy otoki, jeśli istnieje już w bezpiecznej bibliotece klas. Klasa otoki, która musi mieć przyznanie wysokiego stopnia zaufania, aby umożliwić wywołanie do kodu niezarządzanego, jest odpowiedzialna za wymaganie, aby jego wywołujący mieli odpowiednie uprawnienia. Jeśli używasz klasy otoki, kod musi tylko zażądać i uzyskać uprawnienia, których wymaga Klasa otoki.

## <a name="see-also"></a>Zobacz także

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.NamedPermissionSet>
- <xref:System.Security.Permissions.SecurityAction>
- [Stanowcz](using-the-assert-method.md)
- [Zabezpieczenia dostępu kodu](code-access-security.md)
- [Podstawowe informacje o zabezpieczeniach dostępu kodu](code-access-security-basics.md)
- [Atrybuty](../../standard/attributes/index.md)
- [Składniki samoopisujące się i metadane](../../standard/metadata-and-self-describing-components.md)
