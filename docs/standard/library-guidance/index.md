---
title: Wskazówki dotyczące biblioteki .NET typu open-source
description: Zalecenia dotyczące najlepszych rozwiązań dla deweloperów do tworzenia bibliotek platformy .NET o wysokiej jakości.
author: jamesnk
ms.author: mairaw
ms.date: 10/17/2018
ms.openlocfilehash: 85d76c8b2bd0f030e3fbc1987e6ff51d6da44e76
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644382"
---
# <a name="open-source-library-guidance"></a>Wskazówki dotyczące biblioteki typu open-source

Niniejsze wskazówki zawiera zalecenia dla deweloperów do tworzenia bibliotek .NET wysokiej jakości. Ta dokumentacja koncentruje się na *co* i *Dlaczego* podczas kompilowania biblioteki .NET nie *jak*.

Aspekty bibliotek .NET typu open-source wysokiej jakości:

> [!div class="checklist"]
> * **Włączne** -bibliotek .NET dobre Dokładamy wszelkich starań do obsługi wielu platform, programowania języków i aplikacji.
> * **Stabilna** -bibliotek .NET dobre współistnieć w ekosystemie platformy .NET w aplikacji utworzonych za pomocą wielu bibliotek.
> * **Zaprojektowana rozwój** -bibliotek .NET należy poprawić i ewoluować wraz z upływem czasu obsługując istniejących użytkowników.
> * **Debugowalny** -bibliotek .NET Użyj najnowszych narzędzi do tworzenia doskonałe środowisko debugowania dla użytkowników.
> * **Zaufane** -bibliotek .NET mają zaufania deweloperów za publikowanie w usłudze NuGet za pomocą najlepszych rozwiązań dotyczących zabezpieczeń.

> [!div class="nextstepaction"]
> [Wprowadzenie](./get-started.md)

## <a name="types-of-recommendations"></a>Rodzajów zaleceń

Każdy artykuł przedstawia cztery rodzaje zalecenia: **Czy**, **należy wziąć pod uwagę**, **uniknąć**, i **nie**. Typu zalecenie ma do nich wskazuje, jak silnie powinna występować.

Należy wykonać prawie zawsze **czy** zalecenia. Na przykład:

**CZY ✔️** dystrybucji przy użyciu pakietu NuGet biblioteki.

Z drugiej strony **rozważ** ogólnie należy przestrzegać zaleceń, ale istnieje uzasadnione wyjątki od reguły i nie powinien uważasz, że nieprawidłowe o nie postępując zgodnie ze wskazówkami:

**ROZWAŻ ✔️** przy użyciu [SemVer 2.0.0](https://semver.org/) do wersji pakietu NuGet.

**Należy unikać** zalecenia wspomina o identyfikatorach rzeczy, które nie są zwykle dobry pomysł, ale czasami istotne reguła ma sens:

**Należy UNIKAĆ ❌** odwołania do pakietu NuGet, wymagających dokładna wersja.

I wreszcie **nie** zalecenia wskazuje coś prawie nigdy nie należy wykonać:

**❌ NIE** publikowanie o silnych nazwach i innych niż-o silnej nazwie wersji biblioteki. Na przykład `Contoso.Api` i `Contoso.Api.StrongNamed`.

>[!div class="step-by-step"]
>[Next](get-started.md)
