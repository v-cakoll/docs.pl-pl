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
ms.openlocfilehash: a0466eb5c24840c77a3b191f9b0e001f6b267fca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181171"
---
# <a name="link-demands"></a>Żądania połączeń
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Żądanie łącza powoduje sprawdzanie zabezpieczeń podczas kompilacji just-in-time i sprawdza tylko natychmiastowe wywołanie zestawu kodu. Łączenie występuje, gdy kod jest powiązany z odwołaniem do typu, w tym odwołania do wskaźnika funkcji i wywołania metody. Jeśli zestaw wywołujący nie ma wystarczających uprawnień do łącza do kodu, łącze jest niedozwolone i wyjątek środowiska uruchomieniowego jest zgłaszany, gdy kod jest ładowany i uruchamiany. Żądania łącza można zastąpić w klasach, które dziedziczą z kodu.  
  
 Należy zauważyć, że pełny spacer stosu nie jest wykonywane z tego typu popytu i że kod jest nadal podatne na ataki zwabiania. Na przykład jeśli metoda w zestawie A jest chroniony przez żądanie łącza, bezpośrednie obiekt wywołujący w zestawie B jest oceniany na podstawie uprawnień zestawu B.  Jednak zapotrzebowanie na łącza nie oceni metody w zestawie C, jeśli pośrednio wywołuje metodę w zestawie A przy użyciu metody w zestawie B. Żądanie łącza określa tylko uprawnienia bezpośrednich wywołań w zestawie wywołania natychmiastowego musi mieć link do kodu. Nie określa uprawnień, które muszą mieć wszystkie osoby wywołujące do uruchomienia kodu.  
  
 Modyfikatory <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>i <xref:System.Security.CodeAccessPermission.PermitOnly%2A> stack walk nie wpływają na ocenę żądań łączy.  Ponieważ żądania łącza nie wykonują spacer stosu, modyfikatory spacer stosu nie mają wpływu na żądania łącza.  
  
 Jeśli metoda chroniona przez żądanie łącza jest dostępna za pośrednictwem [odbicia,](../reflection-and-codedom/reflection.md)żądanie łącza sprawdza bezpośrednie wywołanie kodu dostępnego za pomocą odbicia. Dotyczy to zarówno odnajdowania metody, jak i wywołania metody wykonywanego przy użyciu odbicia. Załóżmy na przykład, że <xref:System.Reflection.MethodInfo> kod używa odbicia do zwrócenia obiektu reprezentującego metodę chroniona przez żądanie łącza, a następnie przekazuje ten **obiekt MethodInfo** do innego kodu, który używa obiektu do wywołania oryginalnej metody. W takim przypadku sprawdzanie popytu łącza występuje dwa razy: raz dla kodu, który zwraca **MethodInfo** obiektu i raz dla kodu, który wywołuje go.  
  
> [!NOTE]
> Żądanie łącza wykonywane na konstruktorze klasy statycznej nie chroni konstruktora, ponieważ konstruktory statyczne są wywoływane przez system, poza ścieżką wykonywania kodu aplikacji. W rezultacie, gdy żądanie łącza jest stosowane do całej klasy, nie można chronić dostęp do konstruktora statycznego, chociaż nie chroni resztę klasy.  
  
 Poniższy fragment kodu deklaratywnie określa, `ReadData` że każdy `CustomPermission` kod łączący się z metodą musi mieć uprawnienie. To uprawnienie jest hipotetyczne uprawnienie niestandardowe i nie istnieje w .NET Framework. Żądanie jest dokonywane przez przekazanie **SecurityAction.LinkDemand** flagi do `CustomPermissionAttribute`.  
  
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
