---
title: Silne nazewnictwo i biblioteki .NET
description: Najlepsze zalecenia dotyczące silnego nazewnictwa bibliotek .NET.
ms.date: 10/16/2018
ms.openlocfilehash: db268093b07a2ece7cdb8329fd789b52da9c5c32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "76744538"
---
# <a name="strong-naming"></a>Silne nazewnictwo

Silne nazewnictwo odnosi się do podpisywania zestawu za pomocą klucza, tworząc [zestaw o silnej nazwie](../assembly/strong-named.md). Gdy zestaw ma silną nazwę, tworzy unikatową tożsamość na podstawie numeru wersji nazwy i zestawu i może pomóc w zapobieganiu konfliktom zestawów.

Wadą silnego nazewnictwa jest to, że .NET Framework w systemie Windows umożliwia ścisłe ładowanie zestawów, gdy zestaw jest silny. Odwołanie do zestawu o silnej nazwie musi dokładnie odpowiadać wersji, do której odwołuje się zestaw, zmuszając deweloperów do [konfigurowania przekierowań wiązania](../../framework/configure-apps/redirect-assembly-versions.md) podczas korzystania z zestawu:

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

Gdy deweloperzy .NET skarżą się na silne nazewnictwa, co oni zwykle narzekają jest ścisłe ładowanie zestawu. Na szczęście ten problem jest izolowany do .NET Framework. .NET Core, Xamarin, UWP i większość innych implementacji .NET nie mają ścisłego ładowania zestawu i usuwa główną wadę silnego nazewnictwa.

Jednym z ważnych aspektów silnego nazewnictwa jest to, że jest wirusowy: silny nazwany zestaw może odwoływać się tylko do innych silnych zespołów o nazwie. Jeśli biblioteka nie jest silna nazwa, a następnie zostały wykluczone deweloperzy, którzy budują aplikację lub bibliotekę, która wymaga silnego nazewnictwa z niego używać.

Korzyści z silnego nazewnictwa są:

1. Do zestawu można odwoływać się i używać innych zestawów o silnej nazwie.
2. Zestaw może być przechowywany w globalnej pamięci podręcznej zestawów (GAC).
3. Zespół może być ładowany obok siebie z innymi wersjami złożenia. Ładowanie zestawu side-by-side jest często wymagane przez aplikacje z architekturami dodatków plug-in.

## <a name="create-strong-named-net-libraries"></a>Tworzenie silnych nazwanych bibliotek .NET

Należy silnej nazwy bibliotek .NET typu open source. Silne nazewnictwo zestawu zapewnia, że większość osób może go używać, a ścisłe ładowanie zestawu dotyczy tylko .NET Framework.

> [!NOTE]
> Te wskazówki są specyficzne dla publicznie rozpowszechnianych bibliotek .NET, takich jak biblioteki .NET opublikowane w NuGet.org. Silne nazewnictwo nie jest wymagane przez większość aplikacji .NET i nie powinno być wykonywane domyślnie.

✔️ ROZWAŻ silne nazewnictwo zestawów biblioteki.

✔️ ROZWAŻ dodanie silnego klucza nazewnictwa do systemu kontroli źródła.

> Publicznie dostępny klucz umożliwia deweloperom modyfikowanie i ponowne kompilowanie kodu źródłowego biblioteki przy tym samym kluczu.
>
> Nie należy upubliczniać silnego klucza nazewnictwa, jeśli był on używany w przeszłości do nadawania specjalnych uprawnień w [scenariuszach częściowego zaufania.](../../framework/misc/using-libraries-from-partially-trusted-code.md) W przeciwnym razie może naruszyć istniejące środowiska.

> [!IMPORTANT]
> Gdy tożsamość wydawcy kodu jest zalecane [Authenticode](/windows-hardware/drivers/install/authenticode) i [NuGet Podpisywania pakietu](/nuget/create-packages/sign-a-package) są zalecane. Zabezpieczenia dostępu do kodu (CAS) nie powinny być używane jako środki zaradcze zabezpieczeń.

✔️ ZAStanów się nad zwiększaniem wersji zestawu tylko na głównych zmianach wersji, aby pomóc użytkownikom zmniejszyć przekierowanie powiązania i jak często są one aktualizowane.

> Przeczytaj więcej o [wersji i wersji zestawu](./versioning.md#assembly-version).

❌NIE dodawaj, NIE usuwaj ani nie zmieniaj silnego klucza nazewnictwa.

> Modyfikowanie silnego klucza nazewnictwa zestawu zmienia tożsamość zestawu i przerywa skompilowany kod, który go używa. Aby uzyskać więcej informacji, zobacz [zmiany łamania zasad binarnych](./breaking-changes.md#binary-breaking-change).

❌NIE publikuj wersji biblioteki o silnej nazwie i nieo silnej nazwie. Na przykład `Contoso.Api` `Contoso.Api.StrongNamed`i .

> Publikowanie dwóch pakietów rozwidliwek e-systemu deweloperskiego. Ponadto jeśli aplikacja kończy się w zależności od obu pakietów deweloper może napotkać konflikty nazw typów. Jeśli chodzi o .NET dotyczy są różne typy w różnych zestawach.

>[!div class="step-by-step"]
>[Poprzedni](cross-platform-targeting.md)
>[następny](nuget.md)
