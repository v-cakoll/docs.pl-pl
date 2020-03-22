---
title: Bezpieczeństwo i rejestr
ms.date: 07/20/2015
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
ms.openlocfilehash: 454180207d6432e80d87941d1f329f2a4ea7a801
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345485"
---
# <a name="security-and-the-registry-visual-basic"></a>Bezpieczeństwo i rejestr (Visual Basic)

Na tej stronie omówiono implikacje bezpieczeństwa przechowywania danych w rejestrze.  
  
## <a name="permissions"></a>Uprawnienia  

 Przechowywanie wpisów tajnych, takich jak hasła, w rejestrze jako zwykłego tekstu, nie jest bezpieczne, nawet jeśli klucz rejestru jest chroniony listami kontroli dostępu (listami kontroli dostępu).  
  
 Praca z rejestrem może naruszyć bezpieczeństwo, umożliwiając nieodpowiedni dostęp do zasobów systemowych lub chronionych informacji. Aby użyć tych właściwości, musisz mieć uprawnienia do <xref:System.Security.Permissions.RegistryPermissionAccess> odczytu i zapisu z wyliczenia, które kontroluje dostęp do zmiennych rejestru. Każdy kod uruchomiony z pełnym zaufaniem (w ramach domyślnych zasad zabezpieczeń jest to dowolny kod zainstalowany na lokalnym dysku twardym użytkownika) ma niezbędne uprawnienia dostępu do rejestru. Aby uzyskać więcej <xref:System.Security.Permissions.RegistryPermission> informacji, zobacz klasy.  
  
 Zmienne rejestru nie powinny być przechowywane <xref:System.Security.Permissions.RegistryPermission> w lokalizacjach pamięci, gdzie kod bez dostępu do nich. Podobnie podczas udzielania uprawnień, przyznać minimalne uprawnienia niezbędne do wykonania zadania.  
  
 Wartości dostępu do uprawnień <xref:System.Security.Permissions.RegistryPermissionAccess> rejestru są definiowane przez wyliczenie. W poniższej tabeli przedstawiono jej członków.  
  
|Wartość|Dostęp do zmiennych rejestru|  
|-----------|----------------------------------|  
|`AllAccess`|Tworzenie, odczytywanie i pisanie|  
|`Create`|Utwórz|  
|`NoAccess`|Brak dostępu|  
|`Read`|Odczyt|  
|`Write`|Zapisywanie|  
  
## <a name="checking-values-in-registry-keys"></a>Sprawdzanie wartości w kluczach rejestru  

 Podczas tworzenia wartości rejestru, należy zdecydować, co zrobić, jeśli ta wartość już istnieje. Inny proces, być może złośliwy, może już stworzył wartość i mieć do niej dostęp. Po umieszczeniu danych w wartości rejestru dane są dostępne dla innego procesu. Aby temu zapobiec, `GetValue` użyj tej metody. `Nothing` Zwraca, jeśli klucz jeszcze nie istnieje.  
  
> [!IMPORTANT]
> Podczas odczytywania rejestru z aplikacji sieci Web, tożsamość bieżącego użytkownika zależy od uwierzytelniania i personifikacji zaimplementowanych w aplikacji sieci Web.  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [Odczytywanie z rejestru i zapisywanie w nim](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
