---
title: Wskazówki dotyczące biblioteki .NET typu open source
description: Najlepsze zalecenia dla deweloperów do tworzenia bibliotek .NET wysokiej jakości.
ms.date: 10/17/2018
ms.openlocfilehash: 4c76dfae6ffc39df7f15381be64e33657067d79d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "76731422"
---
# <a name="open-source-library-guidance"></a>Wskazówki dotyczące biblioteki typu open-source

Te wskazówki zawierają zalecenia dla deweloperów do tworzenia wysokiej jakości bibliotek .NET. Ta dokumentacja koncentruje się na *co* i *dlaczego* podczas tworzenia biblioteki .NET, a nie *jak*.

Aspekty wysokiej jakości bibliotek open source .NET:

> [!div class="checklist"]
>
> * **Włącznie —** dobre biblioteki .NET starają się obsługiwać wiele platform, języków programowania i aplikacji.
> * **Stabilny** — dobre biblioteki .NET współistnieją w ekosystemie .NET, działające w aplikacjach zbudowanych z wielu bibliotek.
> * **Zaprojektowany do ewolucji** — biblioteki .NET powinny udoskonalać i ewoluować wraz z urazem, jednocześnie obsługując istniejących użytkowników.
> * **Debugowanie** — biblioteki .NET powinny używać najnowszych narzędzi do tworzenia doskonałego środowiska debugowania dla użytkowników.
> * **Zaufane** — biblioteki .NET mają zaufanie deweloperów, publikując w NuGet przy użyciu najlepszych rozwiązań w zakresie zabezpieczeń.

> [!div class="nextstepaction"]
> [Wprowadzenie](./get-started.md)

## <a name="types-of-recommendations"></a>Rodzaje zaleceń

Każdy artykuł przedstawia cztery rodzaje zaleceń: **Czy**, **Należy rozważyć**, **Unikać**, i **nie**. Typ zalecenia wskazuje, jak mocno należy go przestrzegać.

Prawie zawsze należy przestrzegać zalecenia **Do.** Przykład:

✔️ dystrybuują biblioteki przy użyciu pakietu NuGet.

Z drugiej strony **należy wziąć pod uwagę** zalecenia powinny być ogólnie przestrzegane, ale istnieją uzasadnione wyjątki od reguły i nie należy czuć się źle o nie przestrzeganie wskazówek:

✔️ ZASTANÓW SIĘ przy użyciu [SemVer 2.0.0](https://semver.org/) do wersji pakietu NuGet.

**Unikaj** zaleceń wspomnieć rzeczy, które na ogół nie są dobrym pomysłem, ale łamanie reguły czasami ma sens:

❌UNIKAJ nuget odwołań do pakietu, które wymagają dokładnej wersji.

I wreszcie, **Nie** zalecają wskazać coś, czego prawie nigdy nie należy robić:

❌NIE publikuj wersji biblioteki o silnej nazwie i nieo silnej nazwie. Na przykład `Contoso.Api` `Contoso.Api.StrongNamed`i .

>[!div class="step-by-step"]
>[Dalej](get-started.md)
