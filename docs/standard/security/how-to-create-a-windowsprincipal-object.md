---
title: 'Instrukcje: Tworzenie obiektu WindowsPrincipal'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsPrincipal objects, creating
- security [.NET Framework], creating a WindowsPrincipal object
- security [.NET Framework], principals
- principal objects, creating
ms.assetid: 56eb10ca-e61d-4ed2-af7a-555fc4c25a25
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3960a7f87f8ac9a09da7222bd0f7a4a01afc4154
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56583449"
---
# <a name="how-to-create-a-windowsprincipal-object"></a>Instrukcje: Tworzenie obiektu WindowsPrincipal
Istnieją dwa sposoby tworzenia <xref:System.Security.Principal.WindowsPrincipal> obiekt, w zależności od tego, czy kod musi wielokrotnie weryfikowania opartej na rolach lub należy to wykonać tylko raz.  
  
 Jeśli kod musi wykonać wielokrotnie Walidacja oparta na rolach, pierwsza z poniższych procedur powoduje mniejsze obciążenie. Gdy kod musi wprowadzić walidacji opartej na rolach tylko raz, można utworzyć <xref:System.Security.Principal.WindowsPrincipal> obiektu za pomocą drugiego z poniższych procedur.  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a>Do tworzenie obiektu WindowsPrincipal do wielokrotnego sprawdzania poprawności  
  
1.  Wywołaj <xref:System.AppDomain.SetPrincipalPolicy%2A> metody <xref:System.AppDomain> obiekt, który jest zwracany przez statyczną <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> właściwość, przekazując metody <xref:System.Security.Principal.PrincipalPolicy> wartości wyliczenia, która wskazuje, jakie nowe zasady powinny być. Obsługiwane wartości to <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, i <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>. Poniższy kod demonstruje wywołanie tej metody.  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2.  Za pomocą zasad należy ustawić, używa się statycznej <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> właściwość służąca do pobierania jednostki, która hermetyzuje bieżącego użytkownika Windows. Ponieważ typ zwracany przez właściwość <xref:System.Security.Principal.IPrincipal>, należy rzutować wynik, który ma <xref:System.Security.Principal.WindowsPrincipal> typu. Inicjuje nowe wystąpienie następującego kodu <xref:System.Security.Principal.WindowsPrincipal> obiektu do wartości podmiot zabezpieczeń skojarzony z bieżącym wątkiem.  
  
    ```csharp  
    WindowsPrincipal myPrincipal =   
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim myPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)   
    ```  
  
3.  Po utworzeniu obiektu podmiotu zabezpieczeń, można użyć jednej z kilku metod Aby zweryfikować, czy.  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a>Do tworzenie obiektu WindowsPrincipal dla pojedynczego sprawdzania poprawności  
  
1.  Zainicjuj nowe <xref:System.Security.Principal.WindowsIdentity> obiektu przez wywołanie statycznego <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> metody, która odpytuje bieżącego konta Windows, a następnie umieszcza informacji na temat tego konta do obiektu tożsamości nowo utworzony. Poniższy kod tworzy nową <xref:System.Security.Principal.WindowsIdentity> obiektu i inicjuje go do aktualnego użytkownika uwierzytelnionego.  
  
    ```csharp  
    WindowsIdentity myIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim myIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2.  Utwórz nową <xref:System.Security.Principal.WindowsPrincipal> obiektu i przekaż go wartość <xref:System.Security.Principal.WindowsIdentity> obiekt utworzony w poprzednim kroku.  
  
    ```csharp  
    WindowsPrincipal myPrincipal = new WindowsPrincipal(myIdentity);  
    ```  
  
    ```vb  
    Dim myPrincipal As New WindowsPrincipal(myIdentity)  
    ```  
  
3.  Po utworzeniu obiektu podmiotu zabezpieczeń, można użyć jednej z kilku metod Aby zweryfikować, czy.  
  
## <a name="see-also"></a>Zobacz także

- [Obiekty główne i obiekty tożsamości](../../../docs/standard/security/principal-and-identity-objects.md)
