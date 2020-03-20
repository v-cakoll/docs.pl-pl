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
ms.openlocfilehash: 634388e3920e0b9dbee85aa3ea555471cee604ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181117"
---
# <a name="security-and-serialization"></a>Zabezpieczenia i serializacja
Ponieważ serializacja może zezwolić na inne dane wystąpienia lub modyfikowania, które w przeciwnym razie byłyby niedostępne, wymagane jest specjalne uprawnienie do wykonywania serializacji kodu: <xref:System.Security.Permissions.SecurityPermission> z określoną <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> flagą. W obszarze domyślne zasady to uprawnienie nie zostanie podany, do pobieranych przez Internet lub z intranetu kod; to uprawnienie udziela się tylko kod na komputerze lokalnym.  
  
 Zwykle wszystkie pola wystąpienia obiektu są serializowane, co oznacza, że dane są reprezentowane w danych szeregowanych dla wystąpienia. Jest możliwe dla kodu, który można interpretować format, aby określić, jakie są wartości danych, niezależnie od dostępności elementu członkowskiego. Podobnie deserializacji wyodrębnia dane z serializowanej reprezentacji i ustawia stan obiektu bezpośrednio, ponownie niezależnie od reguł ułatwień dostępu.  
  
 Każdy obiekt, który może zawierać dane wrażliwe na zabezpieczenia powinny być nieuprzejme, jeśli to możliwe. Jeśli musi być serializable, spróbuj zrobić określone pola, które przechowują poufne dane nienaserializalne. Jeśli nie można tego zrobić, należy pamiętać, że te dane będą narażone na każdy kod, który ma uprawnienia do serializacji i upewnij się, że żaden złośliwy kod może uzyskać to uprawnienie.  
  
 Interfejs <xref:System.Runtime.Serialization.ISerializable> jest przeznaczony do użytku tylko przez infrastrukturę serializacji. Jednak jeśli nie jest chroniony, może potencjalnie zwolnić poufne informacje. Jeśli podasz niestandardową serializację, implementując **ISerializable,** upewnij się, że podjęto następujące środki ostrożności:  
  
- Metoda <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> powinna być jawnie zabezpieczone przez żądanie **SecurityPermission** z **SerializationFormatter** uprawnienia określone lub upewniając się, że żadne poufne informacje są zwalniane z danych wyjściowych metody. Przykład:  
  
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
  
- Specjalny konstruktor używany do serializacji należy również wykonać dokładne sprawdzanie poprawności danych wejściowych i powinny być chronione lub prywatne, aby pomóc chronić przed niewłaściwym użyciem przez złośliwy kod. Należy wymusić te same kontrole zabezpieczeń i uprawnienia wymagane do uzyskania wystąpienia takiej klasy za pomocą innych środków, takich jak jawne tworzenie klasy lub pośrednio tworzenie go za pośrednictwem pewnego rodzaju fabryki.  
  
## <a name="see-also"></a>Zobacz też

- [Wytyczne dotyczące bezpiecznego programowania](../../standard/security/secure-coding-guidelines.md)
