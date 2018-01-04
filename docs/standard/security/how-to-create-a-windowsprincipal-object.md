---
title: 'Porady: tworzenie obiektu WindowsPrincipal'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsPrincipal objects, creating
- security [.NET Framework], creating a WindowsPrincipal object
- security [.NET Framework], principals
- principal objects, creating
ms.assetid: 56eb10ca-e61d-4ed2-af7a-555fc4c25a25
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c4eb890696162af61f1355bfca50ce5dd2a615ad
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-a-windowsprincipal-object"></a>Porady: tworzenie obiektu WindowsPrincipal
Istnieją dwa sposoby tworzenia <xref:System.Security.Principal.WindowsPrincipal> obiektu, w zależności od tego, czy kod musi wielokrotnie sprawdzania poprawności opartego na rolach lub wykonaj jego tylko raz.  
  
 Jeśli kod wielokrotnie wykonać weryfikacji opartej na rolach, pierwsza z poniższych procedur tworzy mniejsze koszty. Gdy kod musi wprowadzić opartej na rolach sprawdzanie poprawności tylko raz, mogą tworzyć <xref:System.Security.Principal.WindowsPrincipal> obiektu za pomocą drugiego z poniższych procedur.  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a>Aby utworzyć obiekt WindowsPrincipal do weryfikacji powtórzony  
  
1.  Wywołania <xref:System.AppDomain.SetPrincipalPolicy%2A> metoda <xref:System.AppDomain> obiektu, który jest zwracany przez statycznych <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> właściwości przekazywanie metody <xref:System.Security.Principal.PrincipalPolicy> wartość wyliczenia wskazująca, jakie nowych zasad powinny być. Obsługiwane wartości to <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, i <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>. Poniższy kod przedstawia wywołanie tej metody.  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2.  Z zasadami, należy ustawić, użyj statycznych <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> właściwość, aby pobrać podmiot zabezpieczeń, który hermetyzuje bieżącego użytkownika systemu Windows. Ponieważ właściwość zwracany typ jest <xref:System.Security.Principal.IPrincipal>, należy rzutować wynik, który ma <xref:System.Security.Principal.WindowsPrincipal> typu. Poniższy kod inicjuje nowy <xref:System.Security.Principal.WindowsPrincipal> obiektu do wartości podmiot zabezpieczeń skojarzony z bieżącego wątku.  
  
    ```csharp  
    WindowsPrincipal MyPrincipal =   
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim MyPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)   
    ```  
  
3.  Gdy utworzono obiekt główny, umożliwia jedną z kilku metod go zweryfikować.  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a>Aby utworzyć obiekt WindowsPrincipal dla pojedynczego sprawdzania poprawności  
  
1.  Zainicjuj nowy <xref:System.Security.Principal.WindowsIdentity> obiektu przez wywołanie metody statycznych <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> metodę, która wysyła zapytanie do konta systemu Windows i umieszcza informacje o tym koncie w tożsamości nowo utworzony obiekt. Poniższy kod tworzy nową <xref:System.Security.Principal.WindowsIdentity> obiektu i inicjuje ją do bieżącego użytkownika uwierzytelnionego.  
  
    ```csharp  
    WindowsIdentity MyIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim MyIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2.  Utwórz nową <xref:System.Security.Principal.WindowsPrincipal> obiektu i przekaż go wartość <xref:System.Security.Principal.WindowsIdentity> obiekt utworzony w poprzednim kroku.  
  
    ```csharp  
    WindowsPrincipal MyPrincipal = new WindowsPrincipal(MyIdentity);  
    ```  
  
    ```vb  
    Dim MyPrincipal As New WindowsPrincipal(MyIdentity)  
    ```  
  
3.  Gdy utworzono obiekt główny, umożliwia jedną z kilku metod go zweryfikować.  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty główne i obiekty tożsamości](../../../docs/standard/security/principal-and-identity-objects.md)
