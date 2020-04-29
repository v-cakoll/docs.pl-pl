---
ms.openlocfilehash: 7a05f60cf1c04d3d73dadb54541254a83b4ea855
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507096"
---
### <a name="signalr-messagepack-hub-protocol-options-type-changed"></a><span data-ttu-id="590a3-101">Sygnalizacja: Zmieniono typ opcji protokołu MessagePack Hub</span><span class="sxs-lookup"><span data-stu-id="590a3-101">SignalR: MessagePack Hub Protocol options type changed</span></span>

<span data-ttu-id="590a3-102">Typ opcji protokołu MessagePack sygnalizującego "ASP.NET Core" został zmieniony z `IList<MessagePack.IFormatterResolver>` na `MessagePackSerializerOptions` typ biblioteki [MessagePack](https://www.nuget.org/packages/MessagePack) .</span><span class="sxs-lookup"><span data-stu-id="590a3-102">The ASP.NET Core SignalR MessagePack Hub Protocol options type has changed from `IList<MessagePack.IFormatterResolver>` to the [MessagePack](https://www.nuget.org/packages/MessagePack) library's `MessagePackSerializerOptions` type.</span></span>

<span data-ttu-id="590a3-103">Aby uzyskać więcej dyskusji na temat tej zmiany, zobacz [dotnet/aspnetcore # 20506](https://github.com/dotnet/aspnetcore/issues/20506).</span><span class="sxs-lookup"><span data-stu-id="590a3-103">For discussion on this change, see [dotnet/aspnetcore#20506](https://github.com/dotnet/aspnetcore/issues/20506).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="590a3-104">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="590a3-104">Version introduced</span></span>

<span data-ttu-id="590a3-105">5,0 wersja zapoznawcza 4</span><span class="sxs-lookup"><span data-stu-id="590a3-105">5.0 Preview 4</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="590a3-106">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="590a3-106">Old behavior</span></span>

<span data-ttu-id="590a3-107">Możesz dodać do opcji, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="590a3-107">You can add to the options as shown in the following example:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.FormatterResolvers.Add(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

<span data-ttu-id="590a3-108">I Zastąp opcje w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="590a3-108">And replace the options as follows:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.FormatterResolvers = new List<MessagePack.IFormatterResolver>()
        {
            MessagePack.Resolvers.StandardResolver.Instance
        };
    });
```

#### <a name="new-behavior"></a><span data-ttu-id="590a3-109">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="590a3-109">New behavior</span></span>

<span data-ttu-id="590a3-110">Możesz dodać do opcji, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="590a3-110">You can add to the options as shown in the following example:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.SerializerOptions =
            options.SerializeOptions.WithResolver(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

<span data-ttu-id="590a3-111">I Zastąp opcje w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="590a3-111">And replace the options as follows:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.SerializerOptions = MessagePackSerializerOptions
                .Standard
                .WithResolver(MessagePack.Resolvers.StandardResolver.Instance)
                .WithSecurity(MessagePackSecurity.UntrustedData);
    });
```

#### <a name="reason-for-change"></a><span data-ttu-id="590a3-112">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="590a3-112">Reason for change</span></span>

<span data-ttu-id="590a3-113">Ta zmiana jest częścią przejścia do MessagePack v2. x, która została ogłoszona w polu [ASPNET/anonse # 404](https://github.com/aspnet/Announcements/issues/404).</span><span class="sxs-lookup"><span data-stu-id="590a3-113">This change is part of moving to MessagePack v2.x, which was announced in [aspnet/Announcements#404](https://github.com/aspnet/Announcements/issues/404).</span></span> <span data-ttu-id="590a3-114">Biblioteka v2. x dodała interfejs API opcji, który jest łatwiejszy do użycia i udostępnia więcej funkcji niż lista `MessagePack.IFormatterResolver` , która była uwidoczniona wcześniej.</span><span class="sxs-lookup"><span data-stu-id="590a3-114">The v2.x library has added an options API that's easier to use and provides more features than the list of `MessagePack.IFormatterResolver` that was exposed before.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="590a3-115">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="590a3-115">Recommended action</span></span>

<span data-ttu-id="590a3-116">Ta zmiana wpływa na wszystkich użytkowników, którzy konfigurują <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>wartości.</span><span class="sxs-lookup"><span data-stu-id="590a3-116">This breaking change affects anyone who is configuring values on <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.</span></span> <span data-ttu-id="590a3-117">Jeśli używasz protokołu ASP.NET Core sygnalizującego MessagePack i modyfikowania opcji, zaktualizuj użycie, aby użyć nowego interfejsu API opcji, jak pokazano powyżej.</span><span class="sxs-lookup"><span data-stu-id="590a3-117">If you're using the ASP.NET Core SignalR MessagePack Hub Protocol and modifying the options, update your usage to use the new options API as shown above.</span></span>

#### <a name="category"></a><span data-ttu-id="590a3-118">Kategoria</span><span class="sxs-lookup"><span data-stu-id="590a3-118">Category</span></span>

<span data-ttu-id="590a3-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="590a3-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="590a3-120">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="590a3-120">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
