---
title: Sprawdzanie poprawności rejestru nazwy dostawcy
ms.date: 03/30/2017
ms.assetid: c4644dd1-dead-48ff-abeb-7bffae69a6ac
ms.openlocfilehash: fc10181a142fd8ca4ebd8250869d49a046623564
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2019
ms.locfileid: "64910782"
---
# <a name="validating-issuer-name-registry"></a>Sprawdzanie poprawności rejestru nazwy dostawcy
Rozszerzenie Validating Issuer Name Registry (VINR) dla programu Windows Identity Foundation umożliwia aplikacjom wielodostępnym upewnienie się, że przychodzący token został wystawiony przez zaufanego dostawcę dzierżawców i tożsamości. Ta funkcja jest szczególnie przydatna w przypadku aplikacji wielodostępnych, które używają usługi Active Directory systemu Microsoft Azure, ponieważ wszystkie tokeny wystawione przez tę usługę są podpisywane za pomocą tego samego certyfikatu. W celu dokonania rozróżnienia między żądaniami od wielu dzierżawców, którzy korzystają z tego samego certyfikatu — i w związku z tym mają ten sam odcisk palca — aplikacja musi utrwalić nazwę wystawcy dla każdego dzierżawcy, aby wykonać logikę weryfikacji. Rozszerzenie VINR oferuje tę funkcję, a ponadto pozwala na dodawanie niestandardowej logiki weryfikacji lub przechowywanie danych rejestru dostawcy w lokalizacjach innych niż plik konfiguracji. To rozszerzenie można dodać do potoku programu WIF aplikacji lub można go używać niezależnie.  
  
 Rozszerzenie VINR jest dostępne jako pakiet NuGet. Zobacz [Pobieranie pakietu sprawdzania poprawności rejestru nazwy wystawcy](../../../docs/framework/security/downloading-the-validating-issuer-name-registry-package.md) Aby uzyskać więcej informacji.  
  
## <a name="scenarios"></a>Scenariusze  
 Rozszerzenie VINR umożliwia realizację następującego podstawowego scenariusza:  
  
- **Weryfikacja tokenu w aplikacji z wieloma dzierżawami**: W tym scenariuszu firma o nazwie Litware opracowała aplikację wielodostępną, która używa dostawcy tożsamości, takich jak Windows Azure AD. Ta aplikacja obsługuje dwóch klientów: Contoso i Fabrikam. Gdy użytkownik z firmy Fabrikam uwierzytelnia się przed aplikacją firmy Litware, powstały token z usługi AD systemu Microsoft Azure zostaje podpisany przy użyciu standardowego certyfikatu i żądanie zostaje wystawione przez firmę Fabrikam. Aplikacja musi sprawdzić, czy zarówno nazwa wystawcy, jak i token są prawidłowe, i musi odróżniać zapytania z firmy Contoso, które są podpisane za pomocą tego samego certyfikatu z usługi AD systemu Microsoft Azure. Rozszerzenie VINR ułatwia aplikacji firmy Litware odróżnianie i weryfikację żądań od wielu dzierżawców, takich jak Contoso i Fabrikam.  
  
## <a name="features"></a>Funkcje  
 Rozszerzenie VINR oferuje następujące funkcje:  
  
- **Nazwa wystawcy i tokenu weryfikacji dla aplikacji wielodostępnych**: Sprawdza poprawność przychodzącego tokenu przez weryfikację nazwy wystawcy (dzierżawcy) i czy token został podpisany za pomocą ważnego certyfikatu od dostawcy tożsamości.  
  
- **Rozszerzalność logikę niestandardowego sprawdzania poprawności i magazyny danych**: Zapewnia rozszerzalność wstrzyknąć rozszerzyć logikę weryfikacji i określić magazyn danych innego niż domyślny plik konfiguracji.
