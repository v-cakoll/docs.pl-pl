---
title: Wskazówki dotyczące biblioteki .NET Open Source
description: Zalecenia dotyczące najlepszych rozwiązań dla deweloperów do tworzenia bibliotek platformy .NET o wysokiej jakości.
ms.date: 10/17/2018
ms.openlocfilehash: c1e1c302eede86fd5555a8e84630e216e96f1ce7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706455"
---
# <a name="open-source-library-guidance"></a>Wskazówki dotyczące biblioteki typu open-source

Te wskazówki zawierają zalecenia dla deweloperów umożliwiające tworzenie bibliotek platformy .NET o wysokiej jakości. Ta dokumentacja koncentruje się na tym, *co* i *dlaczego* podczas kompilowania biblioteki .NET, a nie w *sposób*.

Aspekty wysokiej jakości bibliotek .NET typu open source:

> [!div class="checklist"]
>
> * **Włączne** — dobre biblioteki .NET dążą do obsługi wielu platform, języków programowania i aplikacji.
> * **Stabilne** i dobre biblioteki platformy .NET współdziałają w ekosystemie platformy .NET, działając w aplikacjach skompilowanych z wieloma bibliotekami.
> * **Zaprojektowana do** rozdzielania bibliotek platformy .NET powinna być ulepszana i zwiększana wraz z upływem czasu obsługi istniejących użytkowników.
> * **Możliwością debugowania** — biblioteki platformy .NET powinny używać najnowszych narzędzi do tworzenia doskonałego środowiska debugowania dla użytkowników.
> * Biblioteki **Zaufane** — .NET mają zaufanie deweloperów, publikując w NuGet przy użyciu najlepszych rozwiązań w zakresie zabezpieczeń.

> [!div class="nextstepaction"]
> [Wprowadzenie](./get-started.md)

## <a name="types-of-recommendations"></a>Typy zaleceń

W każdym artykule przedstawiono cztery typy zaleceń: **czy**należy **rozważyć**, **unikać**i **nie**. Typ zalecenia wskazuje, jak silnie należy postępować.

Prawie zawsze należy **przestrzegać zalecenia.** Na przykład:

**✔️** Przeprowadź dystrybucję biblioteki przy użyciu pakietu NuGet.

Z drugiej strony należy **wziąć pod uwagę** zalecenia, które powinny być przestrzegane, ale istnieją uzasadnione wyjątki wobec reguły i nie należy mieć żadnego nieprzestrzegania wskazówek:

**✔️ rozważyć** użycie programu [SemVer 2.0.0](https://semver.org/) w celu uzyskania wersji pakietu NuGet.

**Należy unikać występowania** zaleceń, które zwykle nie są dobrym pomysłem, ale przerwanie reguły czasami ma sens:

**❌ unikać** Odwołania do pakietu NuGet, które wymagają dokładnej wersji.

A wreszcie **nie są** zalecenia wskazują coś, co należy prawie nigdy nie robić:

**❌** nie publikować wersji z silną nazwą i niesilną nazwą biblioteki. Na przykład `Contoso.Api` i `Contoso.Api.StrongNamed`.

>[!div class="step-by-step"]
>[Next](get-started.md)
