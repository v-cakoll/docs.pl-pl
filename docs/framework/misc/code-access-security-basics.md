---
title: Podstawy zabezpieczeń dostępu kodu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], code access security
ms.assetid: 4eaa6535-d9fe-41a1-91d8-b437cfc16921
ms.openlocfilehash: 08d708e8f98bd2fe06757df3033a512e2fe1f3c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400058"
---
# <a name="code-access-security-basics"></a>Podstawy zabezpieczeń dostępu kodu

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Każda aplikacja, która jest przeznaczona dla środowiska wykonawczego języka wspólnego (czyli każdej aplikacji zarządzanej) musi wchodzić w interakcje z systemem zabezpieczeń środowiska wykonawczego. Po załadowaniu zarządzanej aplikacji jej host automatycznie przyznaje jej zestaw uprawnień. Uprawnienia te są określane przez lokalne ustawienia zabezpieczeń hosta lub przez piaskownicę, w których znajduje się aplikacja. W zależności od tych uprawnień aplikacja działa poprawnie lub generuje wyjątek zabezpieczeń.

Domyślny host dla aplikacji klasycznych umożliwia uruchamianie kodu w pełnym zaufaniu. W związku z tym jeśli aplikacja jest przeznaczona dla pulpitu, ma nieograniczone uprawnienia. Inne hosty lub piaskownice zapewniają ograniczony zestaw uprawnień dla aplikacji. Ponieważ zestaw uprawnień można zmienić z hosta na hosta, należy zaprojektować aplikację, aby używać tylko uprawnienia, które umożliwia host docelowy.

Aby napisać skuteczne aplikacje przeznaczone dla środowiska wykonawczego języka wspólnego, należy zapoznać się z następującymi pojęciami zabezpieczeń dostępu do kodu:

- **Kod bezpieczny dla typu:** Kod bezpieczny dla typu to kod, który uzyskuje dostęp do typów tylko w dobrze zdefiniowany, dozwolony sposób. Na przykład biorąc pod uwagę prawidłowe odwołanie do obiektu, kod bezpieczny dla typu może uzyskać dostęp do pamięci przy stałych przesunięciach, które odpowiadają rzeczywistym członkom pola. Jeśli kod uzyskuje dostęp do pamięci przy dowolnych przesunięciach poza zakresem pamięci, który należy do publicznie narażonych pól tego obiektu, nie jest bezpieczny dla typu. Aby włączyć kod, aby korzystać z zabezpieczeń dostępu do kodu, należy użyć kompilatora, który generuje sprawdzalnie kod bezpieczny dla typu. Aby uzyskać więcej informacji, zobacz [pisanie sprawdzalnie kod bezpieczny dla typu](#typesafe_code) sekcji w dalszej części tego tematu.

- **Imperatywna i deklaratywna składnia:** Kod przeznaczony dla środowiska wykonawczego języka wspólnego może wchodzić w interakcje z systemem zabezpieczeń, żądając uprawnień, żądając, aby obiekty wywołujące mają określone uprawnienia i zastępując niektóre ustawienia zabezpieczeń (biorąc pod uwagę wystarczające uprawnienia). Do programowej interakcji z systemem zabezpieczeń programu .NET Framework używane są dwie formy składni: składnia deklaratywna i składnia imperatywna. Wywołania deklaratywne są wykonywane przy użyciu atrybutów; wywołania imperatyw są wykonywane przy użyciu nowych wystąpień klas w kodzie. Niektóre wywołania mogą być wykonywane tylko bezwzględnie, inne mogą być wykonywane tylko deklaratywnie, a niektóre wywołania mogą być wykonywane w obu przypadkach.

- **Bezpieczne biblioteki klas:** biblioteka klas bezpiecznych używa wymagań zabezpieczeń, aby upewnić się, że osoby wywołujące biblioteki mają uprawnienia dostępu do zasobów udostępnianych przez bibliotekę. Na przykład biblioteka klas bezpiecznych może mieć metodę tworzenia plików, która wymagałaby, aby jej wywołujący mieli uprawnienia do tworzenia plików. .NET Framework składa się z bezpiecznych bibliotek klas. Należy pamiętać o uprawnieniach wymaganych do uzyskania dostępu do dowolnej biblioteki, która używa kodu. Aby uzyskać więcej informacji, zobacz [korzystanie z bibliotek klas bezpiecznych](#secure_library) sekcji w dalszej części tego tematu.

- **Przezroczysty kod:** Począwszy od programu .NET Framework 4, oprócz identyfikowania określonych uprawnień, należy również określić, czy kod powinien być uruchamiany jako przezroczysty dla zabezpieczeń. Kod przezroczysty dla zabezpieczeń nie może wywoływać typów lub członków, które są identyfikowane jako krytyczne dla zabezpieczeń. Ta reguła ma zastosowanie do aplikacji z pełnym zaufaniem, a także częściowo zaufanych aplikacji. Aby uzyskać więcej informacji, zobacz [Kod przezroczysty zabezpieczeń](security-transparent-code.md).

<a name="typesafe_code"></a>

## <a name="writing-verifiably-type-safe-code"></a>Pisanie sprawdzalnie kod bezpieczny dla typu

Kompilacja just-in-time (JIT) wykonuje proces weryfikacji, który sprawdza kod i próbuje ustalić, czy kod jest bezpieczny dla typu. Kod, który jest udowodniony podczas weryfikacji jako bezpieczny dla typu, jest nazywany *sprawdzalnie kodem bezpiecznym*dla typu. Kod może być bezpieczny dla typu, ale może nie być sprawdzalnie bezpieczny dla typu ze względu na ograniczenia procesu weryfikacji lub kompilatora. Nie wszystkie języki są bezpieczne dla typu, a niektóre kompilatory języków, takie jak Microsoft Visual C++, nie mogą generować sprawdzalnie kodu zarządzanego bezpiecznego typu. Aby ustalić, czy używany kompilator języka generuje sprawdzalnie bezpieczny kod, zapoznaj się z dokumentacją kompilatora. Jeśli używasz kompilatora języka, który generuje sprawdzalnie kod bezpieczny dla typu tylko wtedy, gdy można uniknąć niektórych konstrukcji języka, można użyć [peverify narzędzie](../tools/peverify-exe-peverify-tool.md) do określenia, czy kod jest sprawdzalnie typu bezpieczne.

Kod, który nie jest sprawdzalnie typu bezpieczne można spróbować wykonać, jeśli zasady zabezpieczeń umożliwia kod do pomijania weryfikacji. Jednak ponieważ bezpieczeństwo typu jest istotną częścią mechanizmu środowiska wykonawczego do izolowania zestawów, zabezpieczenia nie mogą być niezawodnie wymuszane, jeśli kod narusza reguły bezpieczeństwa typu. Domyślnie kod, który nie jest bezpieczny dla typu, może być uruchamiany tylko wtedy, gdy pochodzi z komputera lokalnego. W związku z tym kod mobilny powinien być bezpieczny dla typu.

<a name="secure_library"></a>

## <a name="using-secure-class-libraries"></a>Korzystanie z bezpiecznych bibliotek klas

Jeśli kod żąda i otrzymuje uprawnienia wymagane przez bibliotekę klas, będzie można uzyskać dostęp do biblioteki i zasoby, które biblioteka udostępnia będą chronione przed nieautoryzowanym dostępem. Jeśli kod nie ma odpowiednich uprawnień, nie będzie mógł uzyskać dostępu do biblioteki klas, a złośliwy kod nie będzie mógł użyć kodu, aby pośrednio uzyskać dostęp do chronionych zasobów. Inny kod, który wywołuje kod musi mieć również uprawnienia dostępu do biblioteki. Jeśli tak się nie stanie, kod będzie również ograniczony do uruchamiania.

Zabezpieczenia dostępu do kodu nie eliminuje możliwość błędu ludzkiego w pisaniu kodu. Jeśli jednak aplikacja używa bibliotek klas bezpiecznych w celu uzyskania dostępu do chronionych zasobów, zmniejsza się ryzyko związane z bezpieczeństwem kodu aplikacji, ponieważ biblioteki klas są dokładnie analizowane pod kątem potencjalnych problemów z zabezpieczeniami.

## <a name="declarative-security"></a>Zabezpieczenia deklaratywne

Deklaratywna składnia zabezpieczeń używa [atrybutów](../../standard/attributes/index.md) do umieszczania informacji zabezpieczających w [metadanych](../../standard/metadata-and-self-describing-components.md) kodu. Atrybuty mogą być umieszczane na poziomie zestawu, klasy lub elementu członkowskiego, aby wskazać typ żądania, popytu lub zastąpienia, którego chcesz użyć. Żądania są używane w aplikacjach, które są przeznaczone dla środowiska wykonawczego języka wspólnego, aby poinformować system zabezpieczeń środowiska wykonawczego o uprawnieniach, które aplikacja potrzebuje lub nie chce. Żądania i zastąpienia są używane w bibliotekach, aby chronić zasoby przed wywoływaniami lub zastąpić domyślne zachowanie zabezpieczeń.

> [!NOTE]
> W .NET Framework 4 wprowadzono ważne zmiany w modelu zabezpieczeń i terminologii programu .NET Framework. Aby uzyskać więcej informacji na temat tych zmian, zobacz [Zmiany zabezpieczeń](../security/security-changes.md).

Aby użyć deklaratywnych wywołań zabezpieczeń, należy zainicjować dane o stanie obiektu uprawnień, tak aby przedstawiał określoną formę uprawnień, których potrzebujesz. Każde wbudowane uprawnienie ma atrybut, <xref:System.Security.Permissions.SecurityAction> który jest przekazywany wyliczenie do opisania typu operacji zabezpieczeń, które chcesz wykonać. Jednak uprawnienia również zaakceptować własne parametry, które są wyłącznie do nich.

Poniższy fragment kodu pokazuje składnię deklaratywną do żądania, `MyPermission`że osoby wywołujące kodu mają niestandardowe uprawnienie o nazwie . To uprawnienie jest hipotetyczne uprawnienie niestandardowe i nie istnieje w .NET Framework. W tym przykładzie deklaratywne wywołanie jest umieszczane bezpośrednio przed definicją klasy, określając, że to uprawnienie ma być stosowane do poziomu klasy. Atrybut jest przekazywany **SecurityAction.Demand** struktury, aby określić, że wywołujący muszą mieć to uprawnienie, aby uruchomić.

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

Imperatyw składni zabezpieczeń powoduje utworzenie wywołania zabezpieczeń przez utworzenie nowego wystąpienia obiektu uprawnień, który chcesz wywołać. Można użyć składni imperatywnej do wykonywania żądań i nadpisań, ale nie żądań.

Przed nawiązaniem wywołania zabezpieczeń należy zainicjować dane o stanie obiektu uprawnień, tak aby przedstawiał określoną formę uprawnienia, którego potrzebujesz. Na przykład podczas tworzenia <xref:System.Security.Permissions.FileIOPermission> obiektu można użyć konstruktora do zainicjowania **FileIOPermission** obiektu tak, aby reprezentuje nieograniczony dostęp do wszystkich plików lub brak dostępu do plików. Można też użyć innego obiektu **FileIOPermission,** przekazując parametry wskazujące typ dostępu, który ma reprezentować obiekt (czyli odczyt, dokłd lub zapis) oraz pliki, które mają być chronione przez obiekt.

Oprócz używania nadrzędnej składni zabezpieczeń do wywoływania pojedynczego obiektu zabezpieczeń, można go użyć do zainicjowania grupy uprawnień w zestawie uprawnień. Na przykład ta technika jest jedynym sposobem, aby niezawodnie wykonywać [wywołania potwierdzenia](using-the-assert-method.md) na wiele uprawnień w jednej metodzie. Użyj <xref:System.Security.PermissionSet> i <xref:System.Security.NamedPermissionSet> klas, aby utworzyć grupę uprawnień, a następnie wywołać odpowiednią metodę, aby wywołać żądane wywołanie zabezpieczeń.

Można użyć składni imperatywnej do wykonywania żądań i nadpisań, ale nie żądań. Można użyć wymaganej składni dla żądań i zastąpienia zamiast składni deklaratywnej, gdy informacje, które są potrzebne do zainicjowania stanu uprawnień staje się znany tylko w czasie wykonywania. Na przykład jeśli chcesz upewnić się, że wywołujący mają uprawnienia do odczytu określonego pliku, ale nie znasz nazwy tego pliku do czasu uruchomienia, użyj żądania imperatywu. Można również użyć kontroli imperatywnej zamiast kontroli deklaratywnej, gdy trzeba określić w czasie wykonywania, czy warunek zawiera i, na podstawie wyniku testu, zażądać zabezpieczeń (lub nie).

Poniższy fragment kodu przedstawia wymaganą składnię żądania, aby osoby wywołujące kodu miały niestandardowe uprawnienie o nazwie `MyPermission`. To uprawnienie jest hipotetyczne uprawnienie niestandardowe i nie istnieje w .NET Framework. Nowe wystąpienie `MyPermission` jest `MyMethod`tworzony w , pilnowanie tylko tej metody z wywołaniem zabezpieczeń.

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

Większość aplikacji i składników (z wyjątkiem bezpiecznych bibliotek) nie należy bezpośrednio wywoływać kod niezarządzany. Jest kilka powodów. Jeśli kod wywołuje kod niezarządzany bezpośrednio, nie będzie można uruchomić w wielu okolicznościach, ponieważ kod musi być przyznawany wysoki poziom zaufania do wywołania kodu macierzystego. Jeśli zasady są modyfikowane w celu umożliwienia uruchamiania takiej aplikacji, może znacznie osłabić bezpieczeństwo systemu, pozostawiając aplikacji swobodę wykonywania prawie każdej operacji.

Ponadto kod, który ma uprawnienia dostępu do kodu niezarządzanego prawdopodobnie można wykonać prawie każdą operację, wywołując w interfejsie API niezarządzane. Na przykład kod, który ma uprawnienia do wywoływania kodu niezarządzanego nie musi <xref:System.Security.Permissions.FileIOPermission> uzyskiwać dostępu do pliku; można po prostu wywołać niezarządzanego (Win32) plik API bezpośrednio, pomijając interfejs API plików zarządzanych, który wymaga **FileIOPermission**. Jeśli kod zarządzany ma uprawnienia do wywoływania kodu niezarządzanego i nie wywołać bezpośrednio do kodu niezarządzanego, system zabezpieczeń nie będzie w stanie niezawodnie wymusić ograniczenia zabezpieczeń, ponieważ środowisko wykonawcze nie może wymusić takich ograniczeń na kod niezarządzany.

Jeśli chcesz, aby aplikacja wykonać operację, która wymaga dostępu do kodu niezarządzanego, należy to zrobić za pośrednictwem zaufanej klasy zarządzanej, która zawija wymagane funkcje (jeśli taka klasa istnieje). Nie należy samodzielnie tworzyć klasy otoki, jeśli istnieje ona już w bibliotece klas bezpiecznych. Klasa otoki, która musi mieć wysoki stopień zaufania, aby umożliwić wywołanie kodu niezarządzanego, jest odpowiedzialna za żądanie, aby jego wywoływanie miały odpowiednie uprawnienia. Jeśli używasz klasy otoki, kod musi tylko zażądać i uzyskać uprawnienia, których wymaga klasa otoki.

## <a name="see-also"></a>Zobacz też

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.NamedPermissionSet>
- <xref:System.Security.Permissions.SecurityAction>
- [Assert](using-the-assert-method.md)
- [Zabezpieczenia dostępu kodu](code-access-security.md)
- [Podstawy zabezpieczeń dostępu kodu](code-access-security-basics.md)
- [Atrybuty](../../standard/attributes/index.md)
- [Składniki samoopisujące się i metadane](../../standard/metadata-and-self-describing-components.md)
