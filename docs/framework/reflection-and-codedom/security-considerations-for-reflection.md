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
ms.openlocfilehash: 9dc7bec2023e3ee0db9987e053dd54647ab2e94f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398707"
---
# <a name="security-considerations-for-reflection"></a>Zagadnienia dotyczące zabezpieczeń dla odbicia
Odbicie pozwala, aby uzyskać informacje o typy i składniki oraz do elementów członkowskich dostępu (to znaczy do wywołania metody i konstruktory do pobierania i ustawiania właściwości wartości, dodawanie i usuwanie programów obsługi zdarzeń i tak dalej). Użyj odbicia w celu uzyskania informacji na temat typów i członków nie jest ograniczone. Cały kod służy odbicia do wykonywania następujących zadań:  
  
-   Wyliczanie typów i członków, a następnie sprawdź ich metadanych.  
  
-   Wyliczanie i sprawdź, czy zestawów i modułów.  
  
 Z kolei za pomocą odbicia do dostępu do elementów członkowskich, podlega ograniczeniom. Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]tylko zaufany kod umożliwia dostęp do elementów członkowskich krytyczny dla zabezpieczeń odbicia. Ponadto tylko zaufany kod może być odbicia niepublicznych elementów członkowskich, które nie jest bezpośrednio dostępny dla skompilowanego kodu dostępu. Na koniec kod, który używa odbicia uzyskać dostępu do członka bezpieczne krytyczne uprawnienia niezależnie od wymagań bezpieczne krytyczne — członek, tylko podobnie jak w przypadku skompilowanego kodu.  
  
 Z zastrzeżeniem odpowiednie uprawnienia kodu można używać odbicia do wykonywania następujące rodzaje dostępu:  
  
-   Dostęp do publicznych elementów członkowskich, które nie są krytyczne dla zabezpieczeń.  
  
-   Członkowie niepubliczni dostępu, które będą dostępne dla skompilowany kod, jeśli te elementy członkowskie nie są krytyczne dla zabezpieczeń. Przykładami takich członkowie niepubliczni:  
  
    -   Chronionych elementów członkowskich klasy podstawowej kodu wywołującego. (W odbicia, to jest nazywany dostęp na poziomie rodziny.)  
  
    -   `internal` elementy członkowskie (`Friend` elementów członkowskich w języku Visual Basic) w zestawie kodu wywołującego. (W odbicia, to jest nazywany dostęp na poziomie zestawu.)  
  
    -   Prywatne elementy Członkowskie inne wystąpienia klasy, która zawiera kod wywołujący.  
  
 Na przykład kodu, który jest uruchamiany w domenie aplikacji piaskownicy jest ograniczona do dostępu opisano w tej listy, chyba że dodatkowe uprawnienia domeny aplikacji.  
  
 Począwszy od [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)], próby uzyskania dostępu do elementów członkowskich, które są niedostępne. zazwyczaj generuje żądanie dla zestawu grant obiektu docelowego plus <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> flagi. Kod, który został uruchomiony z pełnego zaufania (na przykład kod w aplikacji, która jest uruchamiana z poziomu wiersza polecenia) zawsze spełnia te uprawnienia. (To podlega ograniczenia podczas uzyskiwania dostępu do elementów krytycznych dla zabezpieczeń, zgodnie z opisem w dalszej części tego artykułu.)  
  
 Opcjonalnie można przyznać domenie aplikacji piaskownicy <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> Flaga, zgodnie z opisem w sekcji [podczas uzyskiwania dostępu do elementów członkowskich czy są zwykle niedostępny](#accessingNormallyInaccessible)w dalszej części tego artykułu.  
  
<a name="accessingSecurityCritical"></a>   
## <a name="accessing-security-critical-members"></a>Uzyskiwanie dostępu do członków krytyczny dla zabezpieczeń  
 Element członkowski jest krytyczny dla zabezpieczeń, jeśli ma ona <xref:System.Security.SecurityCriticalAttribute>, jeśli należy do typu, który ma <xref:System.Security.SecurityCriticalAttribute>, lub jeśli znajduje się w zestawie krytyczny dla zabezpieczeń. Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], zasady dostępu do członków krytyczny dla zabezpieczeń są następujące:  
  
-   Kod o przezroczystym nie umożliwia odbicia dostęp do elementów członkowskich krytyczny dla zabezpieczeń, nawet jeśli kod jest w pełni zaufany. A <xref:System.MethodAccessException>, <xref:System.FieldAccessException>, lub <xref:System.TypeAccessException> jest generowany.  
  
-   Kod, który został uruchomiony z częściowa relacja zaufania jest traktowany jako przezroczysty.  
  
 Te reguły są takie same, czy uzyskać dostępu bezpośrednio skompilowany kod krytyczny dla zabezpieczeń elementu członkowskiego lub przy użyciu odbicia.  
  
 Kod aplikacji, który jest uruchamiany z poziomu wiersza polecenia są uruchamiane przy pełnym zaufaniu. O ile nie jest oznaczony jako przezroczysty, można użyć do dostęp do elementów członkowskich krytyczny dla zabezpieczeń odbicia. Uruchomienie tego samego kodu z częściowa relacja zaufania (na przykład w domenie aplikacji piaskownicy) zaufania zestawu poziom określa, czy można uzyskać dostęp do kod krytyczny dla zabezpieczeń: Jeśli zestaw ma silną nazwę i jest zainstalowany w globalnej pamięci podręcznej zestawów, zaufane zestawu i może wywołać krytyczny dla zabezpieczeń elementów członkowskich. Jeśli nie jest zaufany, staje się on przezroczysty nawet, jeśli nie została oznaczona jako przezroczysty i nie ma dostępu do członków krytyczny dla zabezpieczeń.  
  
 Aby uzyskać więcej informacji na temat modelu zabezpieczeń w [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], zobacz [zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md).  
  
## <a name="reflection-and-transparency"></a>Odbicie i przezroczystości  
 Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], środowisko uruchomieniowe języka wspólnego określa poziom przezroczystości typu lub elementu członkowskiego kilka czynników, takich jak poziom zaufania zestawu i poziom zaufania domeny aplikacji. Udostępnia odbicia <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Type.IsSecuritySafeCritical%2A>, i <xref:System.Type.IsSecurityTransparent%2A> właściwości, aby umożliwić odnajdowanie poziom przezroczystości typu. W poniższej tabeli przedstawiono prawidłową kombinację tych właściwości.  
  
|Poziom zabezpieczeń|IsSecurityCritical|IsSecuritySafeCritical|IsSecurityTransparent|  
|--------------------|------------------------|----------------------------|---------------------------|  
|Krytyczny|`true`|`false`|`false`|  
|Bezpieczne krytyczne|`true`|`true`|`false`|  
|Przezroczyste|`false`|`false`|`true`|  
  
 Przy użyciu tych właściwości jest znacznie prostsze niż badanie adnotacje zabezpieczeń zestawu i jego typów, sprawdzania na bieżącym poziomie zaufania i próby zduplikowane reguły środowiska uruchomieniowego. Na przykład tego samego typu może być krytyczny dla zabezpieczeń po uruchomieniu z wiersza polecenia lub przezroczystym poziomie bezpieczeństwa, uruchamianych w domenie aplikacji piaskownicy.  
  
 Istnieją podobne właściwości na <xref:System.Reflection.MethodBase>, <xref:System.Reflection.FieldInfo>, <xref:System.Reflection.Emit.TypeBuilder>, <xref:System.Reflection.Emit.MethodBuilder>, i <xref:System.Reflection.Emit.DynamicMethod> klasy. (Inne odbicia i odbicie Emituj obiektów abstrakcyjnych, atrybuty zabezpieczeń są stosowane do skojarzonych z nim metod, na przykład w przypadku właściwości, które są stosowane do metod dostępu właściwości).  
  
<a name="accessingNormallyInaccessible"></a>   
## <a name="accessing-members-that-are-normally-inaccessible"></a>Uzyskiwanie dostępu do elementów członkowskich, które są zwykle niedostępne.  
 Aby użyć odbicia do wywołania elementów członkowskich, które są niedostępne, zgodnie z regułami ułatwień dostępu aparatu plików wykonywalnych języka wspólnego, kodu musi otrzymać jeden z dwóch uprawnienia:  
  
-   Do kodu do dowolnego niepubliczny element członkowski wywołania: musi otrzymać kod <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> flagi.  
  
    > [!NOTE]
    >  Domyślnie zasady zabezpieczeń nie zezwala na to uprawnienie do kodu, które pochodzą z Internetu. To uprawnienie nigdy nie może być przyznany elementowi kodu pochodzącego z Internetu.  
  
-   Kod, aby wywołać żadnych niepubliczny element członkowski, tak długo, jak zestaw grant zestawu, który zawiera wywołany element członkowski jest taka sama jak lub podzbiór, zestaw grant kodu zestawu, który zawiera wywołania: musi otrzymać kod <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>flagi.  
  
 Załóżmy na przykład, udziel uprawnienia Internet plus domeny aplikacji <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> Flaga, a następnie uruchom aplikację internetową z dwóch zestawów, A i B.  
  
-   Zestawu A umożliwia odbicia dostęp do prywatnych elementów członkowskich zestawu B, ponieważ zestaw grant zestawu B nie obejmuje wszystkie uprawnienia, które nie zostało udzielone A.  
  
-   Zestaw A nie umożliwia dostęp do prywatnych elementów członkowskich odbicia [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] zestawy, takie jak mscorlib.dll, ponieważ mscorlib.dll jest w pełni zaufany, a w związku z tym ma uprawnienia, które nie zostały przyznane zestawu A. A <xref:System.MemberAccessException> jest generowany, gdy zabezpieczenia dostępu kodu przedstawiono stosu w czasie wykonywania.  
  
## <a name="serialization"></a>Serializacja  
 Do serializacji <xref:System.Security.Permissions.SecurityPermission> z <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A?displayProperty=nameWithType> Flaga umożliwia pobieranie i ustawianie elementów członkowskich typów możliwych do serializacji, niezależnie od dostępności. To uprawnienie umożliwia kod, aby odnaleźć i zmienić prywatnego stan wystąpienia. (Oprócz trwa odpowiednich uprawnień, typ musi być [oznaczone](../../../docs/standard/attributes/applying-attributes.md) jako możliwy do serializacji w metadanych.)  
  
## <a name="parameters-of-type-methodinfo"></a>Parametry typu MethodInfo.  
 Unikać pisania publiczne elementy członkowskie, które trwają <xref:System.Reflection.MethodInfo> parametrów, szczególnie w przypadku zaufanego kodu. Takie elementy Członkowskie mogą być bardziej podatne na złośliwego kodu. Rozważmy na przykład publicznego elementu członkowskiego w wysoce zaufanych kod, który <xref:System.Reflection.MethodInfo> parametru. Załóżmy, że publicznego elementu członkowskiego pośrednio wymaga <xref:System.Reflection.MethodBase.Invoke%2A> metoda dostarczony parametr. Jeśli publicznego elementu członkowskiego nie przeprowadza kontroli niezbędnych uprawnień, wywołanie <xref:System.Reflection.MethodBase.Invoke%2A> metody zawsze powiedzie się, ponieważ system zabezpieczeń określa, czy element wywołujący jest wysoce zaufanych. Nawet jeśli złośliwego kodu nie ma uprawnienia do bezpośrednio wywołać metody, on nadal należy więc pośrednio przez wywołanie metody publicznego elementu członkowskiego.  
  
## <a name="version-information"></a>Informacje o wersji  
  
-   Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], kod o przezroczystym nie umożliwia dostęp do elementów członkowskich krytyczny dla zabezpieczeń odbicia.  
  
-   <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> Flagi została wprowadzona w systemie [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)]. Starsze niż [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] wymagają <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> flagi kod, który używa odbicia do uzyskiwania dostępu członkowie niepubliczni. To uprawnienie, które nigdy nie może być przyznany elementowi częściowo zaufany kod.  
  
-   Począwszy od [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)], aby uzyskać informacje o niepubliczne typy i składniki przy użyciu odbicia nie wymaga żadnych uprawnień. We wcześniejszych wersjach <xref:System.Security.Permissions.ReflectionPermission> z <xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation?displayProperty=nameWithType> flaga jest wymagana.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.Permissions.ReflectionPermissionFlag>  
 <xref:System.Security.Permissions.ReflectionPermission>  
 <xref:System.Security.Permissions.SecurityPermission>  
 [Zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md)  
 [Zabezpieczenia dostępu kodu](../../../docs/framework/misc/code-access-security.md)  
 [Problemy związane z zabezpieczeniami w emisji odbicia](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
 [Wyświetlanie informacji o typie](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)  
 [Stosowanie atrybutów](../../../docs/standard/attributes/applying-attributes.md)  
 [Uzyskiwanie dostępu do atrybutów niestandardowych](../../../docs/framework/reflection-and-codedom/accessing-custom-attributes.md)
