---
title: Wskazówki dotyczące biblioteki .NET Open Source
description: Zalecenia dotyczące najlepszych rozwiązań dla deweloperów do tworzenia bibliotek platformy .NET o wysokiej jakości.
ms.date: 10/17/2018
ms.openlocfilehash: 4c76dfae6ffc39df7f15381be64e33657067d79d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731422"
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

✔️ Przeprowadź dystrybucję biblioteki przy użyciu pakietu NuGet.

Z drugiej strony należy **wziąć pod uwagę** zalecenia, które powinny być przestrzegane, ale istnieją uzasadnione wyjątki wobec reguły i nie należy mieć żadnego nieprzestrzegania wskazówek:

✔️ ROZWAŻYĆ użycie programu [SemVer 2.0.0](https://semver.org/) w celu uzyskania wersji pakietu NuGet.

**Należy unikać występowania** zaleceń, które zwykle nie są dobrym pomysłem, ale przerwanie reguły czasami ma sens:

❌ UNIKAj odwołań do pakietów NuGet, które wymagają dokładnej wersji.

A wreszcie **nie są** zalecenia wskazują coś, co należy prawie nigdy nie robić:

❌ nie publikować wersji z silną nazwą i niesilną nazwą biblioteki. Na przykład `Contoso.Api` i `Contoso.Api.StrongNamed`.

>[!div class="step-by-step"]
>[Next](get-started.md)
