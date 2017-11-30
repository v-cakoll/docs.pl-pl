---
title: Zabezpieczenia i serializacja
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
- code security, serialization
- serialization, security
- secure coding, serialization
- security [.NET Framework], serialization
ms.assetid: b921bc94-bd3a-4c91-9ede-2c8d4f78ea9a
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9897bbfff542bf708f8fbbc1ac29f7688a1590ac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="security-and-serialization"></a>Zabezpieczenia i serializacja
Ponieważ serializacji można zezwolić na inny kod, aby wyświetlić lub zmodyfikować danych wystąpienia obiektów, które w przeciwnym razie będą niedostępne, specjalnych uprawnień jest wymagane kodu wykonywania serializacji: <xref:System.Security.Permissions.SecurityPermission> z <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> określona flaga. W obszarze domyślne zasady to uprawnienie nie zostanie podany, do pobieranych przez Internet lub z intranetu kod; to uprawnienie udziela się tylko kod na komputerze lokalnym.  
  
 Zwykle wszystkie pola wystąpienia obiektu są serializowane, co oznacza, że dane są reprezentowane w danych serializacji dla tego wystąpienia. Istnieje możliwość kod umożliwiający interpretowanie formatu, aby ustalić, jakie wartości danych są, niezależnie od dostępności elementu członkowskiego. Podobnie deserializacji wyodrębnia dane z zserializowana reprezentacja i ustawia stan obiektu bezpośrednio, ponownie niezależnie od zasady ułatwień dostępu.  
  
 Każdy obiekt, który może zawierać danych istotnych dla zabezpieczeń należy nonserializable, jeśli to możliwe. Jeśli muszą podlegać serializacji, spróbuj wprowadzić określonych pól, które zawierają dane poufne nonserializable. Jeśli nie jest to możliwe, należy pamiętać, że te dane mają być widoczne do kodu, który ma uprawnienia do serializacji i gwarancja, że nie złośliwego kodu to uprawnienie.  
  
 <xref:System.Runtime.Serialization.ISerializable> Interfejsu jest przeznaczony do użytku tylko przez infrastrukturę serializacji. Jednak jeśli niechronionej, jego potencjalnie zwolnić poufne informacje. Jeśli podasz niestandardowej serializacji zaimplementowanie **ISerializable**, upewnij się, podejmij następujące środki ostrożności:  
  
-   <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Metody powinny być jawnie zabezpieczone przez wymagających **SecurityPermission** z **SerializationFormatter** uprawnienia określone lub przez upewniając się, że nie liter informacje o zwolnieniu z danych wyjściowych metody. Na przykład:  
  
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
  
-   Specjalne Konstruktor używany do serializacji należy przeprowadzić dokładne sprawdzania poprawności danych wejściowych i powinien być chroniona lub prywatnej w celu ochrony przed niewłaściwym użyciem przez złośliwy kod. Należy go wymuszać te same testy zabezpieczeń i uprawnienia wymagane do uzyskania wystąpienia takich klasy w inny sposób, takie jak jawne utworzenie klasy lub pośrednio przy użyciu określonego rodzaju fabryki.  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
