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
ms.openlocfilehash: 77687934a91b92909bdbab1ede5075ace4326d4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="code-access-security-basics"></a>Podstawy zabezpieczeń dostępu kodu
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Każda aplikacja, przeznaczonego dla środowiska CLR (oznacza to, co zarządzanych aplikacji) musi współdziałać z systemu zabezpieczeń środowiska uruchomieniowego. Podczas ładowania zarządzanej aplikacji jej host automatycznie spowoduje przyznanie zestaw uprawnień. Te uprawnienia są określane przez hosta ustawienia zabezpieczeń lokalnych lub aplikacji znajduje się w piaskownicy. W zależności od tych uprawnień aplikacja działa prawidłowo lub generuje wyjątek zabezpieczeń.  
  
 Domyślnego hosta dla aplikacji klasycznych umożliwia uruchamianie kodu w trybie pełnego zaufania. W związku z tym, jeśli aplikacja jest przeznaczony dla pulpitu, posiada nieograniczone uprawnienia ustawić. Inne hosty lub piaskownic zapewnia ograniczone uprawnienia ustawione dla aplikacji. Zestaw uprawnień można zmieniać między hostami, należy zaprojektować aplikację do używania uprawnień umożliwiających dostęp do hosta docelowego.  
  
 Należy zapoznać się z następujących koncepcji zabezpieczeń dostępu kodu w celu zapisania obiektu docelowego środowisko uruchomieniowe języka wspólnego skuteczne aplikacji:  
  
-   **Bezpieczny kod**: kod, który uzyskuje dostęp do typów tylko w sposób wyraźnie określone, dozwolony jest bezpieczny kod. Na przykład danego odwołania do prawidłowego obiektu, bezpieczny kod może uzyskiwać dostęp do pamięci w stałej przesunięcia, które odpowiadają elementy członkowskie rzeczywiste pola. Jeśli kod uzyskuje dostęp do pamięci dowolnego przesunięcia poza zakres pamięci należy do tego obiektu publicznie udostępnione pola, nie jest bezpieczne. Aby włączyć kod, aby korzystać z zabezpieczeń dostępu kodu, należy użyć kompilatora, który generuje sprawdzalnie bezpieczny kod. Aby uzyskać więcej informacji, zobacz [zapisu Sprawdzalnie bezpieczny kod](#typesafe_code) później w tym temacie.  
  
-   **Składni konieczne a declarative**: kod, którego celem jest środowisko uruchomieniowe języka wspólnego mogą prowadzić interakcję z systemu zabezpieczeń za pomocą żądania uprawnień wymagających, że obiekty wywołujące określony uprawnienia i zastępowanie niektórych (ustawienia zabezpieczeń Podana wystarczających uprawnień). Użycie dwóch metod składni programowo interakcję z systemu zabezpieczeń .NET Framework: składni deklaratywnej i składni konieczne. Deklaracyjne wywołania są wykonywane przy użyciu atrybutów; wywołania konieczne są wykonywane przy użyciu nowych wystąpień klas w kodzie. Niektóre połączenia, które mogą być wykonywane tylko imperatively, inne mogą być wykonywane tylko deklaratywnie i niektóre połączenia może być wykonane w sposób albo.  
  
-   **Zabezpieczanie bibliotek klas**: biblioteki klas bezpiecznego używa żądania kontroli zabezpieczeń do upewnij się, że wywoływania biblioteki ma uprawnienia dostępu do zasobów, które udostępnia biblioteki. Na przykład biblioteki klas bezpiecznego może mieć metody tworzenia plików, które zażądać, że elementy wywołujące pod mają uprawnienia do tworzenia plików. .NET Framework składa się z bibliotek klas bezpieczne. Należy pamiętać o uprawnienia wymagane do uzyskania dostępu wszystkie biblioteki, który używa Twój kod. Aby uzyskać więcej informacji, zobacz [przy użyciu bibliotek klas Secure](#secure_library) później w tym temacie.  
  
-   **Kod o przezroczystym**: począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], oprócz Identyfikacja określone uprawnienia, należy również określić, czy kod ma być uruchamiana jako przezroczystym poziomie bezpieczeństwa. Kod o przezroczystym poziomie bezpieczeństwa nie można wywołać typów albo elementów członkowskich, które zostały zidentyfikowane jako krytyczny dla zabezpieczeń. Ta reguła ma zastosowanie do pełnego zaufania aplikacji, a także częściowo zaufane aplikacje. Aby uzyskać więcej informacji, zobacz [kod o przezroczystym poziomie bezpieczeństwa](../../../docs/framework/misc/security-transparent-code.md).  
  
<a name="typesafe_code"></a>   
## <a name="writing-verifiably-type-safe-code"></a>Sprawdzalnie bezpieczny kod  
 Just-in-time (JIT) kompilacji wykonuje proces weryfikacji, który sprawdza kod i próbuje określić, czy kod jest bezpieczne. Kodu, która jest podczas weryfikacji za bezpieczne jest nazywany *sprawdzalnie bezpieczny kod*. Kod może być bezpieczne, jeszcze może nie być sprawdzalnie bezpieczny z powodu ograniczenia procesu weryfikacji lub kompilatora. Nie wszystkie języki są bezpieczne, a niektóre Kompilatory języka, takich jak Microsoft Visual C++ nie można wygenerować sprawdzalnie bezpieczny kod zarządzany. Aby ustalić, czy kompilator języka używanego generuje sprawdzalnie bezpieczny kod, zapoznaj się dokumentacją kompilatora. Jeśli używasz kompilatora języka, który generuje sprawdzalnie bezpieczny kod tylko wtedy, gdy uniknąć pewnych konstrukcji języka, możesz chcieć użyć [narzędzie PEVerify](../../../docs/framework/tools/peverify-exe-peverify-tool.md) do ustalenia, czy kod jest sprawdzalnie bezpieczny.  
  
 Kod, który nie jest sprawdzalnie bezpieczny można spróbować wykonać, jeśli zasady zabezpieczeń zezwala na kod, aby pominąć weryfikacji. Jednak ponieważ bezpieczeństwo typów jest integralną część mechanizm izolowanie zestawów środowiska uruchomieniowego, zabezpieczeń nie można niezawodnie wymusić Jeśli kod narusza zasady zabezpieczeń. Domyślnie kod, który nie jest bezpieczne może działać tylko wtedy, gdy pochodzi z komputera lokalnego. W związku z tym przenośnych kod powinien być bezpieczne.  
  
<a name="secure_library"></a>   
## <a name="using-secure-class-libraries"></a>Przy użyciu bibliotek klas bezpieczne  
 Jeśli żądanie kodu i przyznano uprawnienia wymagane przez biblioteki klas, będzie można było uzyskać dostępu do biblioteki i zasoby, które udostępnia biblioteki będą chronione przed nieautoryzowanym dostępem. Jeśli w kodzie nie ma odpowiednich uprawnień, zostanie nie można było uzyskać dostępu do biblioteki klas, a złośliwy kod nie będzie mogła użyć kodu w celu pośredni dostęp do chronionych zasobów. Inny kod, który wywołuje kod musi mieć również uprawnienia dostępu do biblioteki. Jeśli nie, kod będzie dotyczyć również.  
  
 Zabezpieczenia dostępu kodu nie eliminuje możliwości człowieka wystąpił błąd podczas zapisywania kodu. Jednak jeśli aplikacja używa biblioteki klas bezpieczny dostęp do chronionych zasobów, zagrożenie bezpieczeństwa dla kodu aplikacji jest obniżona, ponieważ bibliotek klas są ściśle kontroli dla potencjalnych problemów z zabezpieczeniami.  
  
## <a name="declarative-security"></a>Zabezpieczenia deklaratywne  
 Używa składni zabezpieczenia deklaratywne [atrybuty](../../../docs/standard/attributes/index.md) można umieścić informacji o zabezpieczeniach do [metadanych](../../../docs/standard/metadata-and-self-describing-components.md) kodu. Atrybuty można umieścić na poziomie zestawu, klasa lub element członkowski, aby wskazać typ żądania, żądanie lub zastąpienie, którego chcesz użyć. Żądania są używane w aplikacjach, które odnoszą się do środowiska CLR do informuje system zabezpieczeń środowiska wykonawczego o uprawnieniach wymaganych aplikacji musi lub nie chce. Wymagania i zastąpienia są używane w bibliotekach w celu ochrony zasobów z wywołań lub zastąpienie domyślnego zachowania zabezpieczeń.  
  
> [!NOTE]
>  W [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], zostały ważne zmiany modelu zabezpieczeń .NET Framework i terminologię. Aby uzyskać więcej informacji na temat tych zmian, zobacz [zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md).  
  
 Aby można było używać wywołania zabezpieczenia deklaratywne, należy zainicjować obiektu uprawnienia do danych o stanie, aby reprezentuje danego formularza uprawnień, które są potrzebne. Każdy wbudowanych uprawnień ma atrybut, który jest przekazywany <xref:System.Security.Permissions.SecurityAction> wyliczenie opisujący typ operacji zabezpieczeń, które chcesz wykonać. Uprawnienia zaakceptować również własne parametry, które są na wyłączność dla nich.  
  
 Poniższy fragment kodu przedstawia składni deklaratywnej żądanych wywołań swój kod posiadania uprawnień niestandardowych o nazwie `MyPermission`. To uprawnienie jest hipotetyczny uprawnień niestandardowych i nie istnieje w programie .NET Framework. W tym przykładzie wywołanie deklaratywne znajduje się bezpośrednio przed definicją klasy, określania, czy to uprawnienie można zastosować na poziomie klasy. Ten atrybut jest przekazywany **SecurityAction.Demand** struktury, aby określić, że obiekty wywołujące muszą mieć te uprawnienia, aby można było uruchomić.  
  
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
 Składnia zabezpieczenia imperatywne wystawia wywołania zabezpieczeń, tworząc nowe wystąpienie obiektu uprawnień, które chcesz wywołać. Za pomocą składni konieczne do wykonania żądania i zastąpienia, ale nie żądań.  
  
 Przed wprowadzeniem zabezpieczeń wywołań należy zainicjować obiektu uprawnienia do danych o stanie, aby reprezentuje danego formularza uprawnienia, które są potrzebne. Na przykład podczas tworzenia <xref:System.Security.Permissions.FileIOPermission> obiekt, aby zainicjować można użyć konstruktora **FileIOPermission** obiekt, tak aby reprezentuje albo nieograniczony dostęp do wszystkich plików lub Brak dostępu do plików. Alternatywnie można użyć innego **FileIOPermission** przekazania parametrów, które wskazują na typ dostępu ma obiekt reprezentuje (to znaczy do odczytu, Dołącz lub napisz) i które pliki ma obiekt do ochrony obiektu.  
  
 Oprócz przy użyciu składni zabezpieczenia imperatywne do wywołania obiektu pojedynczego zabezpieczeń, można go zainicjować grupy uprawnień w zestawie uprawnień. Na przykład, ta metoda jest jedynym sposobem niezawodnie wykonać [assert](../../../docs/framework/misc/using-the-assert-method.md) wywołuje na wiele uprawnień w jednej metody. Użyj <xref:System.Security.PermissionSet> i <xref:System.Security.NamedPermissionSet> klasy, aby utworzyć grupę uprawnienia, a następnie wywołać odpowiedniej metody do wywołania wywołania wymaganymi.  
  
 Za pomocą składni konieczne do wykonania żądania i zastąpienia, ale nie żądań. Dla potrzeb może używać składni konieczne i zastępuje zamiast składni deklaratywnej, gdy informacje potrzebne, aby można było zainicjować stan uprawnień staje się znane tylko w czasie wykonywania. Na przykład jeśli chcesz upewnić się, że wywołań ma uprawnienie do odczytu określonego pliku, ale nie znasz nazwę tego pliku do czasu wykonywania, należy użyć nadrzędnych żądanie. Również można Użyj imperatywnych kontroli zamiast deklaratywne kontroli, gdy należy określić w czasie wykonywania, czy warunek jest i, na podstawie wyniku testu, żądanie zabezpieczeń (lub nie).  
  
 Poniższy fragment kodu przedstawia składni konieczne żądanych wywołań swój kod posiadania uprawnień niestandardowych o nazwie `MyPermission`. To uprawnienie jest hipotetyczny uprawnień niestandardowych i nie istnieje w programie .NET Framework. Nowe wystąpienie klasy `MyPermision` jest tworzony w `MyMethod`, ochrona tylko tej metody za pomocą wywołania zabezpieczeń.  
  
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
 Większość aplikacji i składników (z wyjątkiem bezpiecznego bibliotek) nie należy bezpośrednio wywoływać kodu niezarządzanego. Istnieje kilka powodów. Jeśli kod wywołuje bezpośrednio kodu niezarządzanego, nie będzie dozwolone do uruchamiania w wielu sytuacjach, ponieważ kod musi otrzymać wysokiego poziomu zaufania, aby wywoływać kod natywny. Jeśli zasady są modyfikowane w celu zezwolić aplikacji do uruchomienia, znacznie można obniżyć poziom bezpieczeństwa systemu, pozostawiając aplikacji do niemal wszystkich operacji.  
  
 Ponadto kod, który ma uprawnienia umożliwiające dostęp do kodu niezarządzanego prawdopodobnie można wykonać operacji prawie każdego przez wywołanie do niezarządzanego API. Na przykład kod, który ma uprawnienia do wywoływania kodu niezarządzanego nie jest konieczne <xref:System.Security.Permissions.FileIOPermission> dostępu do pliku; ją po prostu Wywołaj niezarządzane (Win32) interfejsu API plików bezpośrednio, pomijanie pliku zarządzanego interfejsu API, która wymaga **FileIOPermission**. Zarządzany kod ma uprawnienie do wywołania do kodu niezarządzanego, wywołać bezpośrednio do kodu niezarządzanego systemu zabezpieczeń będzie mógł niezawodnie wymusić ograniczenia zabezpieczeń, ponieważ środowisko uruchomieniowe nie można wymusić takie ograniczenia dotyczące kodu niezarządzanego.  
  
 Jeśli chcesz aplikacji do wykonywania określonej operacji, która wymaga dostępu do kodu niezarządzanego, go należy to zrobić za pośrednictwem zaufanych zarządzanej klasy, która opakowuje wymaganej funkcjonalności (jeśli istnieje taka klasa). Nie należy tworzyć klasy otoki samodzielnie, jeśli istnieje już w bibliotece klas bezpieczne. Klasa otoki, które muszą być przyznane wysoki stopień zaufania, aby można było wykonać wywołanie do kodu niezarządzanego, jest odpowiedzialny za wymagających, że elementy wywołujące pod mają odpowiednie uprawnienia. Użycie klasy otoki kodu musi tylko do żądania i przyznać uprawnienia, które wymaga klasy otoki.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.PermissionSet>  
 <xref:System.Security.Permissions.FileIOPermission>  
 <xref:System.Security.NamedPermissionSet>  
 <xref:System.Security.Permissions.SecurityAction>  
 [Assert](../../../docs/framework/misc/using-the-assert-method.md)  
 [Zabezpieczenia dostępu kodu](../../../docs/framework/misc/code-access-security.md)  
 [Podstawy zabezpieczeń dostępu kodu](../../../docs/framework/misc/code-access-security-basics.md)  
 [Atrybuty](../../../docs/standard/attributes/index.md)  
 [Składniki samoopisujące się i metadane](../../../docs/standard/metadata-and-self-describing-components.md)
