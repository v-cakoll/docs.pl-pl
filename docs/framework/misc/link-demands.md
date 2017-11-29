---
title: "Żądania połączeń"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: faeeabeda89ea233e67b66b8848f5bbb665d3804
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="link-demands"></a>Żądania połączeń
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Żądanie łącza powoduje, że kontrola zabezpieczeń podczas kompilacji w czasie i sprawdza tylko bezpośredniego wywołującego zestawu kodu. Łączenie występuje, gdy kod jest powiązany z odwołania typu, łącznie z odwołania do wskaźnika funkcji i wywołania metody. Jeśli zestaw wywołujący nie ma wystarczających uprawnień do połączenia w kodzie, łącze jest niedozwolone, a wyjątek czasu wykonywania jest zgłaszany, gdy kod jest załadowany i uruchom. Linkdemand może zostać przesłonięta w klasach, które dziedziczą z kodu.  
  
 Zanotuj przeszukiwania pełnego stosu nie jest wykonywane z tym typem żądanie i czy kod jest nadal podatne na ataki zapewnienia. Na przykład jeśli metoda w zestawie A jest chroniony przez żądanie łącza, bezpośredniego obiektu wywołującego w zestawie B jest obliczane na podstawie uprawnień zestawu B.  Jednak linkdemand nie będą używać metody w zestawie C pośrednio wywołuje metody w zestawie przy użyciu metody w zestawie B. Żądanie łącze Określa, że tylko uprawnienia bezpośrednich wywołań w bezpośredniego wywołującego zestawu musi mieć do połączenia w kodzie. Nie określono uprawnień wszystkim zainteresowanym niezbędne do uruchomienia kodu.  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, I <xref:System.Security.CodeAccessPermission.PermitOnly%2A> Modyfikatory przeszukiwania stosu nie wpływają na obliczanie linkdemand.  Ponieważ linkdemand nie wykonuj przeszukiwania stosu, Modyfikatory przeszukiwania stosu nie mają wpływu na linkdemand.  
  
 Jeśli metoda chroniony przez żądanie łącza jest dostępny za pośrednictwem [odbicia](../../../docs/framework/reflection-and-codedom/reflection.md), żądanie łącza sprawdza bezpośredniego obiektu wywołującego kodu dostępne za pośrednictwem odbicia. Dotyczy to zarówno w przypadku metody odnajdywania, jak i wywołanie metody wykonywane przy użyciu odbicia. Na przykład kodu wykorzystuje odbicia do zwrócenia <xref:System.Reflection.MethodInfo> obiekt reprezentujący metodę chroniony przez żądanie łącza i który następnie przekazuje **MethodInfo** obiekt inny kod używa obiektu można wywołać metody oryginalnego. W takim przypadku sprawdź żądanie łącze występuje dwa razy: raz dla kodu, która zwraca **MethodInfo** obiekt i kod, który wywołuje ona — jeden raz.  
  
> [!NOTE]
>  Żądanie łącza wykonane w konstruktorze klasy statycznej nie chroni konstruktora, ponieważ konstruktory statyczne są wywoływane przez system, poza ścieżka wykonywania kod aplikacji. W związku z tym kiedy żądanie łącza jest stosowany dla całej klasy, nie chroni dostęp do konstruktora statycznego chociaż chronić rest klasy.  
  
 Poniższy fragment kodu deklaratywnie określa żadnego kodu połączenie `ReadData` metoda musi mieć `CustomPermission` uprawnienia. To uprawnienie jest hipotetyczny uprawnień niestandardowych i nie istnieje w programie .NET Framework. Żądanie zostało utworzone przez przekazanie **SecurityAction.LinkDemand** flaga `CustomPermissionAttribute`.  
  
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
 [Atrybuty](../../../docs/standard/attributes/index.md)  
 [Zabezpieczenia dostępu kodu](../../../docs/framework/misc/code-access-security.md)
