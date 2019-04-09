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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2ba3172b1a82c0a9f624a49eb63a193dd29faac1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166994"
---
# <a name="link-demands"></a>Żądania połączeń
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Zapotrzebowania na łącza sprawdza tylko bezpośredniego wywołującego zestawu kodu i powoduje, że sprawdzanie zabezpieczeń podczas kompilacji just in time. Łączenie występuje, gdy kod jest powiązany z odwołaniem typu odwołania do wskaźników funkcji i wywołania metody. Jeśli zestaw wywołujący nie ma wystarczających uprawnień, aby połączyć swój kod, link nie jest dozwolone i wyjątku czasu wykonywania jest zgłaszany, gdy kod jest ładowany i uruchom. Zapotrzebowanie na łącza może zostać przesłonięta w klasach, które dziedziczą z kodu.  
  
 Należy pamiętać, przeszukiwania pełnego stosu nie jest wykonywane przy użyciu tego typu żądanie, oraz że Twój kod jest nadal podatne na ataki zapewnienia. Na przykład jeśli metoda w zestawie A jest chroniony przez żądanie łącza, bezpośredniego obiektu wywołującego w zestawie B jest oceniane na podstawie uprawnień zestawu B.  Jednak zapotrzebowania na łącza nie będą używać metody w zestawie C Jeśli pośrednio wywołuje metodę w zestawie przy użyciu metody w zestawie B. Określa zapotrzebowania na łącza tylko uprawnienia bezpośrednie obiekty wywołujące w bezpośredniego wywołującego zestawu musi mieć do połączenia w kodzie. Nie określa uprawnienia wszystkich obiektów wywołujących niezbędne do uruchomienia kodu.  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, I <xref:System.Security.CodeAccessPermission.PermitOnly%2A> Modyfikatory przeszukiwania stosu nie wpływają na ocena zapotrzebowania na łącza.  Ponieważ zapotrzebowania na łącza nie wykonuj przeszukiwania stosu, Modyfikatory przeszukiwania stosu nie mają wpływu na zapotrzebowanie na łącza.  
  
 Jeśli metoda chroniony przez żądanie łącza odbywa się za pośrednictwem [odbicia](../../../docs/framework/reflection-and-codedom/reflection.md), a następnie zapotrzebowanie na łącza sprawdza bezpośredniego obiektu wywołującego kodu, dostępne za pośrednictwem odbicia. Dotyczy to zarówno metodę odnajdywania, jak i wywołanie metody wykonywane przy użyciu odbicia. Załóżmy, że kod używa odbicia do zwracania <xref:System.Reflection.MethodInfo> obiektu metody reprezentująca chroniona przez żądanie łącza, a następnie przekazuje, **MethodInfo** obiektu do innego kodu, który używa obiektu do oryginalnej metody wywołania. W takim przypadku sprawdź żądanie łącza występuje dwa razy: jeden raz dla kodu, który zwraca **MethodInfo** obiektu i jeden raz dla kodu, który ją wywołuje.  
  
> [!NOTE]
>  Zapotrzebowania na łącza wykonywane w konstruktorze klasy statycznej nie chroni konstruktora, ponieważ konstruktory statyczne są wywoływane przez system, poza ścieżki wykonywania kodu aplikacji. W wyniku stosowania zapotrzebowania na łącza do całej klasy nie chroni dostęp do statycznego konstruktora, mimo że chroni pozostałą część tej klasy.  
  
 Poniższy fragment kodu określa deklaratywne, dowolnego kodu — łączenie `ReadData` metoda musi mieć `CustomPermission` uprawnień. To uprawnienie jest hipotetyczny niestandardowe uprawnienie i nie istnieje w programie .NET Framework. Żądanie jest tworzone przez przekazanie **SecurityAction.LinkDemand** flaga `CustomPermissionAttribute`.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Atrybuty](../../../docs/standard/attributes/index.md)
- [Zabezpieczenia dostępu kodu](../../../docs/framework/misc/code-access-security.md)
