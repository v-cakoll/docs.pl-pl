---
title: Silne nazewnictwo i biblioteki platformy .NET
description: Zalecenia dotyczące najlepszych rozwiązań dotyczących silnych nazw bibliotek platformy .NET.
ms.date: 10/16/2018
ms.openlocfilehash: 0c2dba06413bc6435e3350bf6cc48f1b5882a261
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706429"
---
# <a name="strong-naming"></a>Silne nazewnictwo

Silne nazewnictwo odnosi się do podpisywania zestawu przy użyciu klucza, który wytwarza [zestaw o silnej nazwie](../assembly/strong-named.md). Jeśli zestaw ma silną nazwę, tworzy unikatową tożsamość na podstawie nazwy i numeru wersji zestawu i może pomóc zapobiec konfliktom zestawu.

Minusem do silnego nazewnictwa polega na tym, że .NET Framework w systemie Windows umożliwia ścisłe ładowanie zestawów, gdy zestaw ma silną nazwę. Odwołanie do zestawu o silnej nazwie musi dokładnie pasować do wersji, do której odwołuje się zestaw, wymuszają deweloperom [Konfigurowanie przekierowań powiązań](../../framework/configure-apps/redirect-assembly-versions.md) podczas korzystania z zestawu:

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

Gdy deweloperzy platformy .NET składają się na silne nazewnictwo, to to, czego zwykle są związane z ładowaniem zestawu. Na szczęście ten problem jest odizolowany od .NET Framework. Platformy .NET Core, Xamarin, platformy UWP i większość innych implementacji platformy .NET nie mają ścisłego ładowania zestawu i usuwa główne minusem silnej nazwy.

Jednym ważnym aspektem silnego nazewnictwa jest wirus: silnie nazwany zestaw może odwoływać się tylko do innych silnych nazwanych zestawów. Jeśli biblioteka nie ma silnej nazwy, wykorzystasz deweloperów, którzy tworzą aplikację lub bibliotekę, która wymaga silnego nazewnictwa.

Zalety silnych nazw to:

1. Zestaw może być przywoływany i używany przez inne zestawy o silnych nazwach.
2. Zestaw może być przechowywany w globalnej pamięci podręcznej zestawów (GAC).
3. Zestaw może być ładowany obok innych wersji zestawu. Ładowanie zestawów równoległych jest często wymagane przez aplikacje z architekturą wtyczek.

## <a name="create-strong-named-net-libraries"></a>Tworzenie silnie nazwanych bibliotek platformy .NET

Należy silnej nazwy bibliotek .NET Open Source. Silne nazewnictwo zestawu zapewnia, że większość osób może z niego korzystać, a ścisłe ładowanie zestawu ma wpływ tylko na .NET Framework.

> [!NOTE]
> Te wskazówki dotyczą publicznie dystrybuowanych bibliotek platformy .NET, takich jak biblioteki .NET opublikowane w witrynie NuGet.org. Silne nazewnictwo nie jest wymagane przez większość aplikacji .NET i nie powinno być wykonywane domyślnie.

**✔️ rozważyć** silne nazewnictwo zestawów biblioteki.

**✔️ Rozważ** dodanie klucza silnego nazewnictwa do systemu kontroli źródła.

> Publicznie dostępny klucz umożliwia deweloperom modyfikowanie i ponowne kompilowanie kodu źródłowego biblioteki z tym samym kluczem.
> 
> Klucz silnego nazewnictwa nie powinien być publiczny, jeśli został użyty w przeszłości w celu udzielenia specjalnych uprawnień w [scenariuszach częściowej relacji zaufania](../../framework/misc/using-libraries-from-partially-trusted-code.md). W przeciwnym razie mogą naruszać istniejące środowiska.

> [!IMPORTANT]
> Gdy wymagana jest tożsamość wydawcy kodu, zalecane jest [podpisywanie pakietów](/nuget/create-packages/sign-a-package) [Authenticode](/windows-hardware/drivers/install/authenticode) i NuGet. Zabezpieczeń dostępu kodu (CAS) nie należy używać jako środków zaradczych.

**✔️ rozważyć** zwiększenie wersji zestawu tylko dla głównych zmian wersji, aby ułatwić użytkownikom zredukowanie przekierowań powiązań oraz częstotliwość ich aktualizowania.

> Przeczytaj więcej [na temat przechowywania wersji i wersji zestawu](./versioning.md#assembly-version).

**❌ nie** dodawaj, usuwaj ani nie zmieniaj silnego klucza nazewnictwa.

> Modyfikacja klucza silnego nazewnictwa zestawu zmienia tożsamość zestawu i dzieli skompilowany kod, który go używa. Aby uzyskać więcej informacji, zobacz [binarne zmiany](./breaking-changes.md#binary-breaking-change).

**❌** nie publikować wersji z silną nazwą i niesilną nazwą biblioteki. Na przykład `Contoso.Api` i `Contoso.Api.StrongNamed`.

> Publikowanie dwóch pakietów rozwidlenia systemu dla deweloperów. Ponadto, jeśli aplikacja zostanie zakończona w zależności od obu pakietów, deweloper może napotkać konflikty nazw typów. W odniesieniu do platformy .NET są zainteresowane różne typy w różnych zestawach.

>[!div class="step-by-step"]
>[Poprzedni](cross-platform-targeting.md)
>[Następny](nuget.md)
