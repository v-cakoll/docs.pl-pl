---
title: Zagadnienia dotyczące zabezpieczeń dla odbicia
ms.date: 03/30/2017
helpviewer_keywords:
- permissions [.NET Framework], reflection
- MethodInfo parameters
- reflection, security
- partial trust,reflection
- nonpublic members
- reflection,partial trust
- link demands
ms.assetid: 42d9dc2a-8fcc-4ff3-b002-4ff260ef3dc5
ms.openlocfilehash: 1d5289ce15c213024af576c99fe039f5d6c1a247
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130071"
---
# <a name="security-considerations-for-reflection"></a>Zagadnienia dotyczące zabezpieczeń dla odbicia

Odbicie zapewnia możliwość uzyskiwania informacji o typach i elementach członkowskich, a także do uzyskiwania dostępu do elementów członkowskich (czyli do wywoływania metod i konstruktorów, pobierania i ustawiania wartości właściwości, dodawania i usuwania programów obsługi zdarzeń itd.). Użycie odbicia w celu uzyskania informacji o typach i elementach członkowskich nie jest ograniczone. Cały kod może użyć odbicia, aby wykonać następujące zadania:

- Wyliczanie typów i elementów członkowskich oraz badanie ich metadanych.

- Wyliczanie i sprawdzanie zestawów i modułów.

Użycie odbicia w celu uzyskania dostępu do członków, z kolei podlega ograniczeniom. Począwszy od .NET Framework 4, tylko zaufany kod może używać odbicia w celu uzyskania dostępu do elementów członkowskich o znaczeniu krytycznym. Ponadto tylko zaufany kod może używać odbicia w celu uzyskania dostępu do niepublicznych elementów członkowskich, które nie są bezpośrednio dostępne dla skompilowanego kodu. Na koniec kod, który używa odbicia w celu uzyskania dostępu do elementu członkowskiego o krytycznym znaczeniu, musi mieć wszelkie uprawnienia do bezpiecznego krytycznego zapotrzebowania elementu członkowskiego, podobnie jak w przypadku skompilowanego kodu.

Z zastrzeżeniem niepotrzebnych uprawnień, kod może użyć odbicia, aby wykonać następujące rodzaje dostępu:

- Dostęp do publicznych elementów członkowskich, które nie są krytyczne dla zabezpieczeń.

- Dostęp do niepublicznych elementów członkowskich, które byłyby dostępne dla skompilowanego kodu, jeśli te elementy członkowskie nie są krytyczne dla zabezpieczeń. Przykłady takich niepublicznych członków obejmują:

  - Chronione elementy członkowskie klas bazowych kodu wywołującego. (W odbiciu jest to nazywane dostępem na poziomie rodziny).

  - `internal` członków (`Friend` elementy członkowskie w Visual Basic) w zestawie kodu wywołującego. (W odbiciu jest to określane jako dostęp na poziomie zestawu).

  - Prywatne elementy członkowskie innych wystąpień klasy, które zawierają kod wywołujący.

Na przykład kod, który jest uruchamiany w domenie aplikacji w trybie piaskownicy, jest ograniczony do dostępu opisanego na tej liście, chyba że domena aplikacji przyznaje dodatkowe uprawnienia.

Począwszy od .NET Framework 2,0 z dodatkiem Service Pack 1 próba uzyskania dostępu do elementów członkowskich, które są normalnie niedostępne, generuje żądanie dla zestawu przyznania obiektu docelowego, a <xref:System.Security.Permissions.ReflectionPermission> z flagą <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType>. Kod działający z pełnym zaufaniem (na przykład kod w aplikacji uruchamianej z wiersza polecenia) może zawsze spełniać te uprawnienia. (Jest to uzależnione od ograniczeń w uzyskiwaniu dostępu do elementów członkowskich o znaczeniu krytycznym, zgodnie z opisem w dalszej części tego artykułu).

Opcjonalnie domena aplikacji w trybie piaskownicy może udzielić <xref:System.Security.Permissions.ReflectionPermission> z flagą <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType>, zgodnie z opisem w sekcji [Uzyskiwanie dostępu do elementów członkowskich, które są normalnie niedostępne](#accessingNormallyInaccessible), w dalszej części tego artykułu.

<a name="accessingSecurityCritical"></a>

## <a name="accessing-security-critical-members"></a>Uzyskiwanie dostępu do elementów członkowskich o znaczeniu krytycznym

Składowa ma krytyczne znaczenie dla zabezpieczeń, jeśli ma <xref:System.Security.SecurityCriticalAttribute>, jeśli należy do typu, który ma <xref:System.Security.SecurityCriticalAttribute>, lub jeśli znajduje się w zestawie krytycznym dla zabezpieczeń. Począwszy od .NET Framework 4, reguły uzyskiwania dostępu do elementów członkowskich o znaczeniu krytycznym są następujące:

- Kod przezroczysty nie może używać odbicia w celu uzyskania dostępu do elementów członkowskich o znaczeniu krytycznym, nawet jeśli kod jest w pełni zaufany. Zostanie zgłoszony <xref:System.MethodAccessException>, <xref:System.FieldAccessException>lub <xref:System.TypeAccessException>.

- Kod działający z częściowym zaufaniem jest traktowany jako przezroczysty.

Te reguły są takie same, niezależnie od tego, czy dostęp do elementu członkowskiego o krytycznym znaczeniu jest uzyskiwany bezpośrednio przez skompilowany kod lub do którego można uzyskać dostęp przy użyciu

Kod aplikacji uruchamiany z wiersza polecenia jest uruchamiany z pełnym zaufaniem. O ile nie jest oznaczona jako przezroczysta, może użyć odbicia w celu uzyskania dostępu do elementów członkowskich o znaczeniu krytycznym. Gdy ten sam kod jest uruchamiany z częściowym zaufaniem (na przykład w domenie aplikacji w trybie piaskownicy), poziom zaufania zestawu określa, czy może on uzyskać dostęp do kodu krytycznego dla zabezpieczeń: Jeśli zestaw ma silną nazwę i jest zainstalowany w globalnej pamięci podręcznej zestawów, jest to zaufany zestaw i może wywoływać członków o znaczeniu krytycznym. Jeśli nie jest zaufana, jego stan zmieni się na przezroczysty, mimo że nie został oznaczony jako przezroczysty i nie może uzyskać dostępu do elementów członkowskich o znaczeniu krytycznym.

Aby uzyskać więcej informacji na temat modelu zabezpieczeń w .NET Framework 4, zobacz [zmiany zabezpieczeń](../security/security-changes.md).

## <a name="reflection-and-transparency"></a>Odbicie i przezroczystość

Począwszy od .NET Framework 4, środowisko uruchomieniowe języka wspólnego określa poziom przezroczystości typu lub składowej z kilku czynników, w tym poziom zaufania zestawu i poziom zaufania domeny aplikacji. Odbicie zawiera właściwości <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Type.IsSecuritySafeCritical%2A>i <xref:System.Type.IsSecurityTransparent%2A> umożliwiające odnajdywanie poziomu przezroczystości typu. W poniższej tabeli przedstawiono prawidłowe kombinacje tych właściwości.

|Poziom zabezpieczeń|IsSecurityCritical|IsSecuritySafeCritical|IsSecurityTransparent|
|--------------------|------------------------|----------------------------|---------------------------|
|Krytyczny|`true`|`false`|`false`|
|Bezpieczny-krytyczny|`true`|`true`|`false`|
|Przezroczyste|`false`|`false`|`true`|

Korzystanie z tych właściwości jest znacznie prostsze niż badanie adnotacji zabezpieczeń zestawu i jego typów, sprawdzanie bieżącego poziomu zaufania i próba duplikowania reguł środowiska uruchomieniowego. Na przykład ten sam typ może być krytyczny dla zabezpieczeń, gdy jest uruchamiany z wiersza polecenia lub jest przezroczysty dla zabezpieczeń, gdy jest uruchamiany w domenie aplikacji w trybie piaskownicy.

Istnieją podobne właściwości dla klas <xref:System.Reflection.MethodBase>, <xref:System.Reflection.FieldInfo>, <xref:System.Reflection.Emit.TypeBuilder>, <xref:System.Reflection.Emit.MethodBuilder>i <xref:System.Reflection.Emit.DynamicMethod>. (W przypadku innych abstrakcji emisji odbicia i odbicia, atrybuty zabezpieczeń są stosowane do skojarzonych metod, na przykład w przypadku właściwości, które są stosowane do dostępu do właściwości).

<a name="accessingNormallyInaccessible"></a>

## <a name="accessing-members-that-are-normally-inaccessible"></a>Uzyskiwanie dostępu do elementów członkowskich, które są zwykle niedostępne

Aby użyć odbicia do wyzwolenia elementów członkowskich, które są niedostępne zgodnie z regułami dostępności środowiska uruchomieniowego języka wspólnego, kod musi mieć przyznany jeden z dwóch uprawnień:

- Aby umożliwić programowi Code wywoływanie dowolnego niepublicznego elementu członkowskiego: kod musi być przyznany <xref:System.Security.Permissions.ReflectionPermission> ze flagą <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType>.

  > [!NOTE]
  > Domyślnie zasady zabezpieczeń odmówią tego uprawnienia do kodu pochodzącego z Internetu. To uprawnienie nigdy nie powinno być udzielane kodowi pochodzącemu z Internetu.

- Aby umożliwić programowi Code wywoływanie niepublicznego elementu członkowskiego, pod warunkiem, że zestaw dotacji zestawu, który zawiera wywołany element członkowski, jest taki sam jak lub podzbiór, zestaw przyznany zestaw, który zawiera kod wywołujący: kod musi być udzielony <xref:System.Security.Permissions.ReflectionPermission> ze flagą <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>.

Załóżmy na przykład, że przyznano uprawnienia internetowe domeny aplikacji oraz <xref:System.Security.Permissions.ReflectionPermission> z flagą <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>, a następnie uruchomisz aplikację internetową z dwoma zestawami, a i B.

- Zestaw A może używać odbicia w celu uzyskania dostępu do prywatnych składowych zestawu B, ponieważ zestaw przypisań zestawu B nie zawiera żadnych uprawnień, których nie udzielono.

- Zestaw A nie może używać odbicia w celu uzyskania dostępu do prywatnych elementów członkowskich zestawów .NET Framework, takich jak mscorlib. dll, ponieważ biblioteka mscorlib. dll jest w pełni zaufana i w związku z tym ma uprawnienia, które nie zostały przyznane do zestawu A. Zostanie zgłoszony <xref:System.MemberAccessException>, gdy zabezpieczenia dostępu kodu przeprowadzi stos w czasie wykonywania.

## <a name="serialization"></a>Serializacja

W przypadku serializacji <xref:System.Security.Permissions.SecurityPermission> z flagą <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A?displayProperty=nameWithType> umożliwia pobieranie i ustawianie elementów członkowskich typu możliwego do serializacji, niezależnie od ułatwień dostępu. To uprawnienie umożliwia kod w celu odnalezienia i zmiany stanu prywatnego wystąpienia. (Oprócz przyznania odpowiednich uprawnień, typ musi być [oznaczony](../../standard/attributes/applying-attributes.md) jako możliwy do serializacji w metadanych).

## <a name="parameters-of-type-methodinfo"></a>Parametry typu MethodInfo

Unikaj pisania publicznych elementów członkowskich, które pobierają <xref:System.Reflection.MethodInfo> parametry, szczególnie w przypadku kodu zaufanego. Takie składowe mogą być bardziej podatne na złośliwy kod. Rozważmy na przykład publiczną składową w wysoce zaufanym kodzie, który przyjmuje <xref:System.Reflection.MethodInfo> parametr. Załóżmy, że publiczna składowa pośrednio wywołuje metodę <xref:System.Reflection.MethodBase.Invoke%2A> dla podanego parametru. Jeśli publiczny element członkowski nie wykonuje wymaganych kontroli uprawnień, wywołanie metody <xref:System.Reflection.MethodBase.Invoke%2A> zawsze powiedzie się, ponieważ system zabezpieczeń ustali, że obiekt wywołujący jest wysoce zaufany. Nawet jeśli złośliwy kod nie ma uprawnień do bezpośredniego wywoływania metody, można to zrobić pośrednio przez wywołanie publicznego elementu członkowskiego.

## <a name="version-information"></a>Informacje o wersji

- Począwszy od .NET Framework 4 przezroczysty kod nie może używać odbicia w celu uzyskania dostępu do elementów członkowskich o znaczeniu krytycznym.

- Flaga <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> została wprowadzona w dodatku Service Pack 1 dla .NET Framework 2,0. Wcześniejsze wersje .NET Framework wymagają flagi <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> dla kodu, który używa odbicia w celu uzyskania dostępu do niepublicznych elementów członkowskich. Jest to uprawnienie, które nigdy nie powinno zostać przyznane do częściowo zaufanego kodu.

- Począwszy od .NET Framework 2,0, używanie odbicia w celu uzyskania informacji na temat typów niepublicznych i członków nie wymaga żadnych uprawnień. We wcześniejszych wersjach jest wymagane <xref:System.Security.Permissions.ReflectionPermission> z flagą <xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation?displayProperty=nameWithType>.

## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Permissions.ReflectionPermissionFlag>
- <xref:System.Security.Permissions.ReflectionPermission>
- <xref:System.Security.Permissions.SecurityPermission>
- [Zmiany zabezpieczeń](../security/security-changes.md)
- [Zabezpieczenia dostępu kodu](../misc/code-access-security.md)
- [Problemy związane z zabezpieczeniami w emisji odbicia](security-issues-in-reflection-emit.md)
- [Wyświetlanie informacji o typie](viewing-type-information.md)
- [Stosowanie atrybutów](../../standard/attributes/applying-attributes.md)
- [Uzyskiwanie dostępu do atrybutów niestandardowych](accessing-custom-attributes.md)
