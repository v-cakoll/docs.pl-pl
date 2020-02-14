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
ms.openlocfilehash: cb0ba120eeb57788c0525d45b714ad8edd2c39ed
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216974"
---
# <a name="security-and-serialization"></a>Zabezpieczenia i serializacja
Ponieważ Serializacja może zezwalać innemu kodowi na wyświetlanie lub modyfikowanie danych wystąpienia obiektu, które w przeciwnym razie byłyby niedostępne, wymagane jest specjalne uprawnienie do kodu wykonującego serializację: <xref:System.Security.Permissions.SecurityPermission> z flagą <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> określoną. W obszarze domyślne zasady to uprawnienie nie zostanie podany, do pobieranych przez Internet lub z intranetu kod; to uprawnienie udziela się tylko kod na komputerze lokalnym.  
  
 Zwykle wszystkie pola wystąpienia obiektu są serializowane, co oznacza, że dane są reprezentowane w serializowanych danych dla tego wystąpienia. Możliwe jest, że kod, który może interpretować format, aby określić, jakie wartości danych są niezależne od dostępności elementu członkowskiego. Podobnie deserializacja wyodrębnia dane z serializowanej reprezentacji i bezpośrednio ustawia stan obiektu, niezależnie od zasad dostępu.  
  
 Każdy obiekt, który może zawierać dane zależne od zabezpieczeń, powinien być niemożliwy do serializacji, jeśli jest to możliwe. Jeśli musi to być możliwe do serializacji, spróbuj wprowadzić określone pola, które mają dane poufne, które nie mogą być serializowane. Jeśli nie można tego zrobić, należy pamiętać, że te dane zostaną uwidocznione w dowolnym kodzie, który ma uprawnienia do serializacji, i upewnić się, że żaden złośliwy kod nie może uzyskać tego uprawnienia.  
  
 Interfejs <xref:System.Runtime.Serialization.ISerializable> jest przeznaczony do użycia tylko przez infrastrukturę serializacji. Jednak w przypadku niechronionego programu może on potencjalnie zwolnić poufne informacje. W przypadku zapewnienia serializacji niestandardowej przez implementację interfejsu **ISerializable**upewnij się, że są wykonywane następujące środki ostrożności:  
  
- Metoda <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> powinna być jawnie zabezpieczona przez wymaganie **SecurityPermission** z uprawnieniami **SerializationFormatter** z określonym lub przez upewnienie się, że żadne poufne informacje nie są zwalniane przy użyciu danych wyjściowych metody. Na przykład:  
  
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
  
- Specjalny Konstruktor używany do serializacji powinien również wykonywać dokładne sprawdzanie poprawności danych wejściowych i powinien być chroniony lub prywatny, aby pomóc w ochronie przed nieprawidłowym użyciem złośliwego kodu. Należy wymusić te same sprawdzenia zabezpieczeń i uprawnienia wymagane do uzyskania wystąpienia takiej klasy w inny sposób, na przykład w celu jawnego utworzenia klasy lub pośredniego tworzenia jej za pośrednictwem pewnego rodzaju fabryki.  
  
## <a name="see-also"></a>Zobacz też

- [Wytyczne dotyczące bezpiecznego programowania](../../standard/security/secure-coding-guidelines.md)
