---
title: Konfiguracja scentralizowana
description: Centralna konfiguracja przy użyciu Azure Key Vault może ułatwić zarządzanie aplikacjami natywnymi w chmurze.
ms.date: 06/30/2019
ms.openlocfilehash: 4c516b6773d913acd71ff06742302e9766a141e2
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71213999"
---
# <a name="centralized-configuration"></a>Konfiguracja scentralizowana

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Aplikacje natywne w chmurze obejmują wiele innych działających usług niż tradycyjne aplikacje monolityczne o pojedynczej instancji. Zarządzanie ustawieniami konfiguracji dla dziesiątek usług zależnych może być trudne, co oznacza, że scentralizowane magazyny konfiguracji są często zaimplementowane dla aplikacji rozproszonych.

Zgodnie z opisem w [rozdziale 1](introduction.md)rekomendacje dotyczące aplikacji 12-Factor wymagają ścisłego rozdzielenia kodu i konfiguracji. Oznacza to, że przechowywanie ustawień konfiguracji jako stałych lub wartości literałów w kodzie jest naruszeniem. To zalecenie istnieje, ponieważ ten sam kod powinien być używany w wielu środowiskach, takich jak programowanie, testowanie, przygotowanie i produkcja. Jednak wartości konfiguracyjne mogą się różnić w zależności od tego środowiska. Dlatego wartości konfiguracyjne powinny być przechowywane w samym środowisku lub środowisko powinno przechowywać poświadczenia w scentralizowanym magazynie konfiguracji.

Aplikacja eShopOnContainers obejmuje lokalne pliki ustawień aplikacji z każdą mikrousługą. Te pliki są sprawdzane w kontroli źródła, ale nie zawierają wpisów tajnych produkcji, takich jak parametry połączenia lub klucze interfejsu API. W środowisku produkcyjnym poszczególne ustawienia mogą zostać zastąpione zmiennymi środowiskowymi dla poszczególnych usług. Jest to typowa procedura dla hostowanych aplikacji, ale nie zapewnia centralnego magazynu konfiguracji. Aby zapewnić obsługę scentralizowanego zarządzania ustawieniami konfiguracji, każda mikrousługa zawiera ustawienie umożliwiające przełączenie między użyciem ustawień lokalnych lub Azure Key Vault ustawień.

## <a name="azure-key-vault"></a>Usługa Azure Key Vault

Azure Key Vault zapewnia bezpieczny magazyn tokenów, haseł, certyfikatów, kluczy interfejsu API i innych poufnych wpisów tajnych. Dostęp do Key Vault wymaga właściwego uwierzytelniania i autoryzacji wywołującego, co w przypadku mikrousług eShopOnContainers oznacza użycie kombinacji ClientId/ClientSecret. Nie sprawdzaj tych poświadczeń w kontroli źródła, ale zamiast tego ustaw je w środowisku aplikacji. Bezpośredni dostęp do Key Vault z AKS można osiągnąć przy użyciu [Key Vault FlexVolume](https://github.com/Azure/kubernetes-keyvault-flexvol).

W przypadku scentralizowanej konfiguracji ustawienia, które mają zastosowanie do całej aplikacji, takie jak scentralizowany punkt końcowy rejestrowania, mogą być ustawiane raz i używane przez każdą część aplikacji rozproszonej. Chociaż mikrousługi powinny być niezależne od siebie, zazwyczaj nadal są niektóre współużytkowane zależności, których szczegóły konfiguracji mogą korzystać z scentralizowanego magazynu konfiguracji.

>[!div class="step-by-step"]
>[Poprzedni](deploy-eshoponcontainers-azure.md)
>[Następny](scale-applications.md)
