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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 34f0002554320f99d961d03e9eebd8d0f774f1f6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591514"
---
# <a name="security-considerations-for-reflection"></a>Zagadnienia dotyczące zabezpieczeń dla odbicia
Odbicie umożliwia uzyskanie informacji dotyczących typów i elementów członkowskich i dostęp do elementów członkowskich (czyli do wywołania metod i konstruktorów do pobierania i ustawiania właściwości wartości, dodawanie i usuwanie programów obsługi zdarzeń i tak dalej). Użycie odbicia w celu uzyskania informacji na temat typów i elementów członkowskich nie jest ograniczona. Cały kod może używać odbicia do wykonywania następujących zadań:  
  
- Wyliczanie typów i elementów członkowskich i zbadaj ich metadanych.  
  
- Wyliczanie i badania zestawów i modułów.  
  
 Z drugiej strony, przy użyciu odbicia do dostępu do elementów członkowskich, podlega ograniczeniom. Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]należy korzystać tylko z zaufanego kodu umożliwia dostęp do elementów członkowskich zabezpieczenia krytyczny odbicia. Ponadto tylko zaufanego kodu można użyć odbicia do połączenia niepubliczne elementy członkowskie, które nie będą dostępne dla kodu skompilowanego. Na koniec kod, który używa odbicia na uzyskiwanie dostępu do członka bezpieczny krytyczny musi mieć uprawnienia, niezależnie od wymagań bezpieczny krytyczny element członkowski, po prostu, podobnie jak w przypadku skompilowany kod.  
  
 Z zastrzeżeniem odpowiednie uprawnienia kod może użyć odbicia przeprowadzić następujące rodzaje dostępu:  
  
- Dostęp do publicznych składowych, które nie są krytyczne dla bezpieczeństwa.  
  
- Członkowie niepubliczni dostępu, które będą dostępne dla kodzie skompilowanym, jeśli te elementy członkowskie nie są krytyczne dla bezpieczeństwa. Przykłady takich niepubliczne elementy członkowskie:  
  
    - Chronione składowe klas bazowych kodu wywołującego. (W odbiciu, to nazywa się dostęp na poziomie rodziny.)  
  
    - `internal` elementy członkowskie (`Friend` elementów członkowskich w języku Visual Basic) w zestawie wywołującego kodu. (W odbiciu, to nazywa się dostęp na poziomie zestawu.)  
  
    - Prywatnych składowych innych wystąpień klasy, która zawiera kod wywołujący.  
  
 Na przykład kod uruchomiony w domenie aplikacji w trybie piaskownicy jest ograniczona do dostępu opisanego na tej liście, chyba, że domena aplikacji przyznaje dodatkowe uprawnienia.  
  
 Począwszy od [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)], próby uzyskania dostępu do elementów członkowskich, które są zwykle niedostępne generuje zapotrzebowanie na zestaw uprawnień obiektu docelowego wynosząca <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> flagi. Kod, który jest uruchomiony z pełnym zaufaniem (na przykład, kod w aplikacji, który jest uruchamiany z wiersza polecenia) zawsze może spełnić te uprawnienia. (To jest zastrzeżeniem ograniczeń podczas uzyskiwania dostępu do elementów członkowskich zabezpieczenia krytyczny, zgodnie z opisem w dalszej części tego artykułu).  
  
 Opcjonalnie można przyznać domeny aplikacji w trybie piaskownicy <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> Flaga, zgodnie z opisem w sekcji [uzyskiwania dostępu do elementów członkowskich, są zwykle niedostępne](#accessingNormallyInaccessible), w dalszej części tego artykułu.  
  
<a name="accessingSecurityCritical"></a>   
## <a name="accessing-security-critical-members"></a>Uzyskiwanie dostępu do elementów krytycznych dla zabezpieczeń  
 Element członkowski jest krytyczne dla bezpieczeństwa, jeśli ma ona <xref:System.Security.SecurityCriticalAttribute>, jeśli należy do typu, który ma <xref:System.Security.SecurityCriticalAttribute>, lub jeśli znajduje się w zestawie zabezpieczenia krytyczny. Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], zasady do uzyskiwania dostępu do zabezpieczenia krytyczny elementów członkowskich są następujące:  
  
- Przezroczysty kod nie można użyć odbicia dostęp do elementów członkowskich zabezpieczenia krytyczny, nawet jeśli kod jest w pełni zaufany. A <xref:System.MethodAccessException>, <xref:System.FieldAccessException>, lub <xref:System.TypeAccessException> zgłaszany.  
  
- Kod, który został uruchomiony z częściowej relacji zaufania jest traktowane jako przezroczyste.  
  
 Te zasady są takie same, czy dostępne bezpośrednio przez skompilowany kod zabezpieczenia krytyczny elementu członkowskiego lub uzyskiwać dostęp przy użyciu odbicia.  
  
 Kod aplikacji, uruchamianego z wiersza polecenia jest uruchamiany z pełnym zaufaniem. Tak długo, jak nie jest oznaczony jako przezroczysty, ona używać odbicia na dostęp do elementów członkowskich zabezpieczenia krytyczny. Po uruchomieniu ten sam kod z częściowej relacji zaufania (na przykład w domenie aplikacji w trybie piaskownicy) poziom zaufania zestawu Określa, czy można uzyskać dostęp do kod zabezpieczenia krytyczny: Jeśli zestaw ma silną nazwę i jest zainstalowany w globalnej pamięci podręcznej, jest zaufanym zestawie i wywołując elementy członkowskie krytyczne dla bezpieczeństwa. Jeśli nie jest zaufany, staje się przezroczyste nawet, jeśli nie została oznaczona jako przezroczysty, a nie może uzyskać dostępu członków zabezpieczenia krytyczny.  
  
 Aby uzyskać więcej informacji o modelu zabezpieczeń w [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], zobacz [zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md).  
  
## <a name="reflection-and-transparency"></a>Odbicia i przejrzystości  
 Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], środowisko uruchomieniowe języka wspólnego określa poziom przezroczystości typu lub elementu członkowskiego z kilkoma czynnikami, w tym poziom zaufania zestawu i poziom zaufania domeny aplikacji. Odbicie umożliwia <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Type.IsSecuritySafeCritical%2A>, i <xref:System.Type.IsSecurityTransparent%2A> właściwości, aby umożliwić odnajdowanie poziom przezroczystości typu. W poniższej tabeli przedstawiono prawidłowe kombinacje tych właściwości.  
  
|Poziom zabezpieczeń|IsSecurityCritical|IsSecuritySafeCritical|IsSecurityTransparent|  
|--------------------|------------------------|----------------------------|---------------------------|  
|Krytyczny|`true`|`false`|`false`|  
|Safe-critical|`true`|`true`|`false`|  
|Przezroczyste|`false`|`false`|`true`|  
  
 Korzystanie z tych właściwości jest znacznie prostsze niż badanie adnotacje zabezpieczeń zestawu i jego typów, sprawdzania bieżącego poziomu zaufania i próby zduplikowania reguł w środowisku uruchomieniowym. Na przykład ten sam typ może być zabezpieczenia krytyczny po jej uruchomieniu z wiersza polecenia lub przezroczyste dla zabezpieczeń, po uruchomieniu w domenie aplikacji w trybie piaskownicy.  
  
 Istnieją podobne właściwości na <xref:System.Reflection.MethodBase>, <xref:System.Reflection.FieldInfo>, <xref:System.Reflection.Emit.TypeBuilder>, <xref:System.Reflection.Emit.MethodBuilder>, i <xref:System.Reflection.Emit.DynamicMethod> klasy. (Inne odbicia i odbicia abstrakcje emisji, atrybuty zabezpieczeń są stosowane do skojarzonego metod, na przykład w przypadku właściwości, które są stosowane do metody dostępu właściwości).  
  
<a name="accessingNormallyInaccessible"></a>   
## <a name="accessing-members-that-are-normally-inaccessible"></a>Uzyskiwanie dostępu do elementów członkowskich, które są zwykle niedostępne.  
 Użycie odbicia w celu wywołania elementów członkowskich, które są niedostępne, zgodnie z regułami dostępność środowiska uruchomieniowego języka wspólnego, kod musi otrzymać jeden dwa uprawnienia:  
  
- Aby umożliwić kodu do wywołania dowolnego niepubliczna składowa: kod musi mieć przyznane <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> flagi.  
  
    > [!NOTE]
    >  Domyślnie zasady zabezpieczeń nie zezwala na tego uprawnienia, aby kod, który pochodzi z Internetu. To uprawnienie nigdy nie może być przyznany do kodu, który pochodzi z Internetu.  
  
- Zezwalaj na kod do wywołania dowolnego niepubliczna składowa tak długo, jak zestaw uprawnień zestawu, który zawiera wywołanego elementu członkowskiego jest taka sama jak lub być podzbiorem wartości, zestaw uprawnień w zestawie, który zawiera wywoływanie kodu: Twój kod musi mieć przyznane <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> flagi.  
  
 Załóżmy na przykład, można przyznać domeny aplikacji oraz uprawnienia Internet <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> Flaga, a następnie uruchom aplikację internetową za pomocą dwóch zestawów, A i B.  
  
- Zestaw A umożliwia odbicia dostęp do prywatnych elementów członkowskich zestawu B, ponieważ zestaw uprawnień zestaw B nie zawiera żadnych uprawnień, które nie udzielono A.  
  
- Zestaw, A nie umożliwia dostęp do prywatnych elementów członkowskich odbicia [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] zestawy, takie jak mscorlib.dll, ponieważ biblioteka mscorlib.dll jest w pełni zaufany i dlatego ma uprawnienia, które nie zostały przyznane do zestawu A. Element <xref:System.MemberAccessException> jest zgłaszany, gdy zabezpieczenia dostępu kodu przedstawiono stosu w czasie wykonywania.  
  
## <a name="serialization"></a>Serializacja  
 Do serializacji <xref:System.Security.Permissions.SecurityPermission> z <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A?displayProperty=nameWithType> Flaga umożliwia pobieranie i ustawianie elementów członkowskich typów możliwych do serializacji, niezależnie od tego, w ułatwienia dostępu. To uprawnienie umożliwia kodu odnaleźć i zmienić prywatnego stanu wystąpienia. (Oprócz trwa odpowiednich uprawnień, należy określić typ [oznaczone](../../../docs/standard/attributes/applying-attributes.md) jako możliwy do serializacji w metadanych.)  
  
## <a name="parameters-of-type-methodinfo"></a>Parametry MethodInfo — typ  
 Należy unikać pisania publiczne elementy członkowskie, które trwają <xref:System.Reflection.MethodInfo> parametrów, szczególnie w przypadku zaufanego kodu. Takie elementy Członkowskie mogą być bardziej podatne na złośliwego kodu. Na przykład, należy wziąć pod uwagę publicznej składowej w wysoce zaufanym kodem, który przyjmuje <xref:System.Reflection.MethodInfo> parametru. Przyjęto założenie, że publiczny członek pośrednio wywołuje <xref:System.Reflection.MethodBase.Invoke%2A> metody na podany parametr. Jeśli publicznej składowej nie przeprowadza kontroli niezbędnych uprawnień, wywołanie <xref:System.Reflection.MethodBase.Invoke%2A> metody zawsze powiedzie się, ponieważ system zabezpieczeń określa, czy obiekt wywołujący jest wysoce zaufane. Nawet jeśli złośliwy kod nie ma uprawnień do bezpośrednio wywołać metody, jego nadal należy więc pośrednio przez wywołanie metody publicznej składowej.  
  
## <a name="version-information"></a>Informacje o wersji  
  
- Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], kod przezroczysty nie może używać odbicia w celu dostęp do elementów członkowskich zabezpieczenia krytyczny.  
  
- <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> Flagi została wprowadzona w systemie [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)]. Wcześniejszych wersjach [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] wymagają <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> flagi dla kodu, który używa odbicia, aby dostęp do elementów członkowskich niepublicznych. Jest to uprawnienia, które nigdy nie może być przyznany elementowi częściowo zaufanego kodu.  
  
- Począwszy od [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)], przy użyciu odbicia w celu uzyskania informacji na temat niepublicznych typy i elementy członkowskie nie wymaga żadnych uprawnień. We wcześniejszych wersjach <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation?displayProperty=nameWithType> flaga jest wymagana.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Permissions.ReflectionPermissionFlag>
- <xref:System.Security.Permissions.ReflectionPermission>
- <xref:System.Security.Permissions.SecurityPermission>
- [Zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md)
- [Zabezpieczenia dostępu kodu](../../../docs/framework/misc/code-access-security.md)
- [Problemy związane z zabezpieczeniami w emisji odbicia](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)
- [Wyświetlanie informacji o typie](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
- [Stosowanie atrybutów](../../../docs/standard/attributes/applying-attributes.md)
- [Uzyskiwanie dostępu do atrybutów niestandardowych](../../../docs/framework/reflection-and-codedom/accessing-custom-attributes.md)
