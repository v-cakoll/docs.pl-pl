---
title: Żądania połączeń
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], demands
- demanded permissions
- permissions [.NET Framework], demands
- granting permissions, demands
- code access security, demands
- user demands for permission
- caller security checks
- link demands
ms.assetid: a33fd5f9-2de9-4653-a4f0-d9df25082c4d
ms.openlocfilehash: 31fbd938acb457a4ea803375d18cb1be11d8b287
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217168"
---
# <a name="link-demands"></a>Żądania połączeń
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Żądanie linku powoduje sprawdzenie zabezpieczeń podczas kompilacji just-in-Time i sprawdza tylko bezpośrednio wywołujący zestaw kodu. Łączenie występuje, gdy kod jest powiązany z odwołaniem do typu, w tym odwołaniami wskaźników funkcji i wywołaniami metod. Jeśli zestaw wywołujący nie ma wystarczających uprawnień do łączenia się z kodem, link jest niedozwolony i podczas ładowania i uruchamiania kodu zostanie wygenerowany wyjątek czasu wykonywania. Wymagania dotyczące linków można przesłonić w klasach, które dziedziczą z kodu.  
  
 Należy zauważyć, że pełne przechodzenie stosu nie jest przeprowadzane z tym typem żądania i że kod nadal jest podatny na ataki luring. Na przykład jeśli metoda w zestawie A jest chroniona przez żądanie linku, bezpośredni obiekt wywołujący w zestawie B jest oceniany na podstawie uprawnień zestawu B.  Jednak żądanie linku nie będzie szacować metody w zestawie C, jeśli pośrednio wywołuje metodę w zestawie A przy użyciu metody w zestawie B. Żądanie linku określa tylko elementy wywołujące bezpośrednich uprawnień w bezpośrednim wywołującym zestawie musi mieć połączenie z kodem. Nie określa uprawnień, które mogą być wymagane do uruchomienia kodu.  
  
 Modyfikatory przeszukiwania stosu <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>i <xref:System.Security.CodeAccessPermission.PermitOnly%2A> nie wpływają na ocenę żądań związanych z łączami.  Ponieważ wymagania dotyczące linków nie wykonują przechodzenia stosu, Modyfikatory przeszukiwania stosu nie mają wpływu na wymagania dotyczące linków.  
  
 Jeśli dostęp do metody chronionej przez żądanie linku odbywa się za pomocą [odbicia](../reflection-and-codedom/reflection.md), żądanie linku sprawdza natychmiastowy obiekt wywołujący kod, do którego uzyskano dostęp za pomocą odbicia. Dotyczy to zarówno odnajdywania metody, jak i wywołania metody wykonywanej przy użyciu odbicia. Załóżmy na przykład, że kod używa odbicia do zwrócenia obiektu <xref:System.Reflection.MethodInfo> reprezentującego metodę chronioną przez żądanie linku, a następnie przekazuje ten obiekt **MethodInfo** do innego kodu, który używa obiektu do wywołania pierwotnej metody. W takim przypadku sprawdzanie wymagań linku odbywa się dwa razy: raz dla kodu, który zwraca obiekt **MethodInfo** i jeden raz dla kodu, który go wywołuje.  
  
> [!NOTE]
> Żądanie linku wykonywane na konstruktorze klasy statycznej nie chroni konstruktora, ponieważ konstruktory statyczne są wywoływane przez system, poza ścieżką wykonywania kodu aplikacji. W związku z tym, gdy żądanie linku jest stosowane do całej klasy, nie może chronić dostępu do konstruktora statycznego, chociaż chroni resztę klasy.  
  
 Poniższy fragment kodu deklaratywnie określa, że dowolny kod łączący się z metodą `ReadData` musi mieć uprawnienie `CustomPermission`. To uprawnienie jest hipotetycznym uprawnieniem niestandardowym i nie istnieje w .NET Framework. Żądanie jest wykonywane przez przekazanie flagi **SecurityAction. LinkDemand** do `CustomPermissionAttribute`.  
  
```vb  
<CustomPermissionAttribute(SecurityAction.LinkDemand)> _  
Public Shared Function ReadData() As String  
    ' Access a custom resource.  
End Function    
```  
  
```csharp  
[CustomPermissionAttribute(SecurityAction.LinkDemand)]  
public static string ReadData()  
{  
    // Access a custom resource.  
}  
```  
  
## <a name="see-also"></a>Zobacz też

- [Atrybuty](../../standard/attributes/index.md)
- [Zabezpieczenia dostępu kodu](code-access-security.md)
