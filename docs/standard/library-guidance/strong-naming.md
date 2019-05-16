---
title: Silne nazewnictwo i bibliotek platformy .NET
description: Zalecenia dotyczące najlepszych rozwiązań dla silnego nazewnictwa bibliotek platformy .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/16/2018
ms.openlocfilehash: 79e44e89a94c1948ff29b9a8161f852c3a7c8cbb
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65640791"
---
# <a name="strong-naming"></a>Silne nazewnictwo

Silne nazwy odwołuje się do podpisywania zestawu za pomocą klucza, tworzenie [zestawu z silną nazwą](../../framework/app-domains/strong-named-assemblies.md). W przypadku zestawu o silnej nazwie, tworzy unikatową tożsamość na podstawie numeru wersji nazwy i zestawu, a może pomóc zapobiec konfliktom zestawu.

Wadą do silne nazwy jest .NET Framework na Windows umożliwia strict ładowania zestawów, gdy zestaw ma silną nazwę. Odwołanie do zestawu z silną nazwą musi dokładnie odpowiadać wersji odwołuje się zestaw wymuszanie deweloperom [Konfigurowanie przekierowania powiązań](../../framework/configure-apps/redirect-assembly-versions.md) korzystając z zestawu:

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
         <dependentAssembly>
            <assemblyIdentity name="myAssembly" publicKeyToken="32ab4ba45e0a69a1" culture="neutral" />
            <bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0"/>
         </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

W przypadku deweloperów platformy .NET narzekają — silne nazwy, co to są one zazwyczaj skarżących o jest strict ładowania zestawu. Na szczęście tego problemu jest izolowane do programu .NET Framework. .NET core, Xamarin, platformy uniwersalnej systemu Windows i większości innych implementacji .NET nie mają ściśle z ładowaniem zestawu i usuwa głównego wadą — silne nazwy.

Ważnym aspektem — silne nazwy jest wirusowe: silna o nazwie zestawu mogą odwoływać się tylko inne silne nazwanych zestawów. Jeśli biblioteka nie jest silne o nazwie, zostały wykluczone deweloperzy, którzy tworzą aplikację lub bibliotekę, która potrzebuje — silne nazwy korzystanie z niego.

Zalety — silne nazwy to:

1. Zestaw można odwołanie i używany przez inne zestawy o silnych nazwach.
2. Zestaw mogą być przechowywane w globalnej pamięci podręcznej zestawów (GAC).
3. Zestaw można załadować równolegle z innymi wersjami zestawu. Ładowanie zestawu Side-by-side często jest wymagane przez aplikacje za pomocą wtyczki architektury.

## <a name="create-strong-named-net-libraries"></a>Utwórz silne o nazwie bibliotek platformy .NET

Strong należy nadać nazwę bibliotek .NET typu open source. Silne nazewnictwo zestawu zapewnia większość użytkowników będzie można jej używać, i tylko z ładowaniem zestawu, ograniczeniami ma wpływ na .NET Framework.

> [!NOTE]
> Niniejsze wskazówki dotyczy publicznie rozpowszechniane bibliotek .NET, takich jak biblioteki .NET opublikowane w witrynie NuGet.org. Silne nazwy nie jest wymagane przez większość aplikacji .NET i nie należy wykonywać domyślnie.

**ROZWAŻ ✔️** silnych nazw zestawów biblioteki.

**ROZWAŻ ✔️** Dodawanie silnych nazw klucz do systemu kontroli źródła.

> Publicznie dostępne klucz umożliwia deweloperom zmodyfikować i ponownie skompilować kod źródłowy biblioteki za pomocą tego samego klucza.
> 
> Nie należy wprowadzeniu silnych nazw klucz publiczny, jeśli został on użyty w przeszłości do nadania uprawnienia specjalne w [scenariuszy częściowego zaufania](/dotnet/framework/misc/using-libraries-from-partially-trusted-code). W przeciwnym razie może spowodować naruszenie istniejących środowisk.

> [!IMPORTANT]
> Gdy tożsamość wydawcy kodu, [Authenticode](/windows-hardware/drivers/install/authenticode) i [podpisywanie pakietów NuGet](/nuget/create-packages/sign-a-package) są zalecane. Zabezpieczeń dostępu kodu (CAS) nie powinien służyć jako ograniczenia zabezpieczeń.

**ROZWAŻ ✔️** zwiększanie wersji zestawu na zmiany wersji jedyny duży, aby ułatwić użytkownikom zmniejszenie przekierowania powiązań i jak często są aktualizowane.

> Przeczytaj więcej na temat [przechowywanie wersji i wersję zestawu](./versioning.md#assembly-version).

**❌ NIE** dodać, usunąć lub zmienić silnego klucza nazewnictwa.

> Modyfikowanie zestawu silnego nazewnictwa klucza tożsamości zestawu zmian i przerywa skompilowany kod, który korzysta z niego. Aby uzyskać więcej informacji, zobacz [binarne istotne zmiany w](./breaking-changes.md#binary-breaking-change).

**❌ NIE** publikowanie o silnych nazwach i innych niż-o silnej nazwie wersji biblioteki. Na przykład `Contoso.Api` i `Contoso.Api.StrongNamed`.

> Publikowanie oba pakiety rozwidlenia ekosystemu usługi dla deweloperów. Ponadto jeśli aplikacji, kończy się w zależności od tego, oba pakiety Deweloper mogą wystąpić konflikty nazw typu. Chodzi .NET jest są różnych typów w różnych zestawach.

>[!div class="step-by-step"]
>[Poprzednie](cross-platform-targeting.md)
>[dalej](nuget.md)
