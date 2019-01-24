---
title: Zabezpieczenia i serializacja
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, serialization
- serialization, security
- secure coding, serialization
- security [.NET Framework], serialization
ms.assetid: b921bc94-bd3a-4c91-9ede-2c8d4f78ea9a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 996231ae035e6518aaceac0ba75b3de3b52a0a22
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640176"
---
# <a name="security-and-serialization"></a>Zabezpieczenia i serializacja
Ponieważ serializacji może pozwalać na inny kod wyświetlić lub zmodyfikować dane wystąpienia obiektu, która mogłaby być niedostępna, specjalne uprawnienie jest wymagane wykonywanie serializacji kodu: <xref:System.Security.Permissions.SecurityPermission> z <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> określono flagę. W obszarze domyślne zasady to uprawnienie nie zostanie podany, do pobieranych przez Internet lub z intranetu kod; to uprawnienie udziela się tylko kod na komputerze lokalnym.  
  
 Normalnie wszystkie pola wystąpienia obiektu są serializowane, co oznacza, że dane są reprezentowane w danych serializacji dla tego wystąpienia. Istnieje możliwość dla kodu, który może interpretować formatu, aby ustalić, jakie wartości danych są, niezależnie od dostępności członka. Podobnie deserializacji wyodrębnia dane z zserializowana reprezentacja i ustawia stan obiektu bezpośrednio, ponownie niezależnie od zasady ułatwień dostępu.  
  
 Dowolny obiekt, który może zawierać dane istotnymi dla zabezpieczeń należy nonserializable, jeśli jest to możliwe. Jeśli muszą podlegać serializacji, spróbuj wprowadzić określonych pól zawierających dane poufne nonserializable. Jeśli nie jest to możliwe, należy pamiętać, że te dane będą widoczne wszelki kod, który ma uprawnienia do serializacji i upewnij się, czy nie złośliwego kodu można uzyskać to uprawnienie.  
  
 <xref:System.Runtime.Serialization.ISerializable> Interfejsu jest przeznaczony do użytku tylko przez infrastrukturę serializacji. Jednak jeśli bez ochrony, jego potencjalnie zwalniać poufne informacje. Jeśli podasz niestandardowej serializacji implementując **ISerializable**, upewnij się, należy wykonać następujące środki ostrożności:  
  
-   <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Metody powinny być jawnie zabezpieczone przez wymagających **SecurityPermission** z **SerializationFormatter** uprawnienie określono lub przez upewniając się, że nie liter informacje o zwolnieniu z danymi wyjściowymi metody. Na przykład:  
  
    ```vb  
    Public Overrides<SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)>  _  
    Sub GetObjectData(info As SerializationInfo, context As StreamingContext)  
    End Sub  
    ```  
  
    ```csharp  
    [SecurityPermissionAttribute(SecurityAction.Demand,SerializationFormatter   
    =true)]  
    public override void GetObjectData(SerializationInfo info,   
    StreamingContext context)  
    {  
    }  
    ```  
  
-   Specjalnych konstruktora, używanych na potrzeby serializowania również należy wykonać dokładne sprawdzenie poprawności danych wejściowych i powinna być chroniona lub prywatnej, aby chronić przed niewłaściwym użyciem przez złośliwy kod. Powinien on wymuszać samą kontroli bezpieczeństwa i uprawnienia wymagane do uzyskania wystąpienia takich klasy za pomocą innych środków, takich jak jawne utworzenie klasy lub pośrednio ją przy użyciu pewnego rodzaju fabryki.  
  
## <a name="see-also"></a>Zobacz także
- [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
