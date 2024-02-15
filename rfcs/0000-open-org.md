# Open Nix organisation

Scratch space: https://pad.lassul.us/LLDT7BrRS8yE0p9ruU3_tw?edit

## Summary

Create a public repository to be the source of truth for the Nix organisation, declaring who and what is part of it and who owns what.
This gives a central place to allow anybody to discuss the organisation and propose changes to it.

## Motivation

### No process for new official projects

Currently there is no good process by which new projects can be made official.

There's three ways this could be done now, each with their pro
- Directly ask somebody with the right permissions for it.

  This is not great because it's not clear _who_ has the right permissions,
  and the people with the right permissions are rightfully hesitant to agree to such ad-hoc requests.

  However this does sometimes happen, e.g. when @zimbatm created the [nixpkgs-merge-bot](https://github.com/nixos/nixpkgs-merge-bot) GitHub repository was created [at OceanSprint](https://discourse.nixos.org/t/announcing-nixpkgs-merge-bot/34265).
  
- Use the [RFC process](https://github.com/NixOS/rfcs) to declare a new project official,
  after which somebody with the right permissions should have no hesitation to set it up.

  This is not great because RFCs have a high overhead and cause a significant toll on the authors/shepherds, often ending up as stalled.
  Especially in our volunteer-based community, we shouldn't force people to waste their time on such processes if they can be avoided.
  
  Still, this has been used in the past with the [RFC for using Matrix](https://github.com/NixOS/rfcs/blob/master/rfcs/0094-use-matrix-for-official-chat.md),
  and is being used still in the [official Nix standard format RFC](https://github.com/NixOS/rfcs/pull/166).
  
- Ask the NixOS Foundation board by opening an issue on [their issue tracker](https://github.com/NixOS/foundation/issues).

  This is not great because the board is [not responsible for technical decisions](https://nixos.org/community/teams/foundation-board)
  and has previously [abstained from making such decisions](https://github.com/NixOS/foundation/issues/113#issuecomment-1919684335)
  (though it's [unclear whether this is a technical decision](https://github.com/NixOS/foundation/issues/113#issuecomment-1910759938) in general).
  Furthermore, the board is severely limited in their resources and has [a lot on their plate](https://github.com/NixOS/foundation/issues) already.

  This has [been attempted](https://github.com/NixOS/foundation/issues/113) for an uncontroversial topic with some success,
  but with general agreement that a better process is needed, which this RFC will give.

### Process for archiving old projects

Currently there's no good process to archive old projects.

The recent [teams collaboration effort](https://github.com/NixOS/teams-collaboration) started by @thufschmitt has seen some success.
After general agreement in the meetings, [issues in various GitHub repos were opened](https://github.com/NixOS/teams-collaboration/issues/1) to ask for status, with @thufschmitt's intention to write a script to automate the archival for most of them.

### Unclear how to get permissions

There's currently no good general process for receiving permissions to help out with official efforts.

Some different approaches exist, with various degrees of success:

- Specifically for Nixpkgs, an ad-hoc process has emerged:
  Since 2019, [this GitHub issue](https://github.com/NixOS/nixpkgs/issues/50105) has been the standard way to nominate people for commit access,
  using emoji reactions to indicate ones support for a nomination.
  Every once in a while, @domenkozar gives commit rights to the uncontroversial nominees.
  This is how ~150 (~75%) of people got commit access.
    
  While the interface for this isn't great, this has clearly demonstrated that this process works.

- Another similar success story is the RFC Steering committee, which creates a [yearly public discussion](https://discourse.nixos.org/t/rfc-steering-committee-rotation-2023-24/36197) for new people to nominate themselves as members.
  New members are then picked by consensus among existing members.

- What can also work is for the people with sufficient permissions to notice people that could make good use of extra permissions, and willingly handing them out without an explicit nomination.

  While this isn't very reliable, there are examples of this working out.

- The fallback is directly asking the people with the sufficient permissions to give them permissions.

  On GitHub, the org owners definitely can,
  but this permission can also be handed out to others, which is the case for certain teams/repos.
  
  In general it's really not clear who can do that and one needs to look and ask around to find out.
  Especially if we consider non-GitHub permissions, such as social media accounts, DNS records, etc.
  
  It's also much more tricky for central permissions such as GitHub org owners.

### Unclear how to lose permissions

There's currently no good process for proposing for people to lose certain permissions.
While this isn't often necessary, it is sometimes.

For Nixpkgs, there have been at least [three public instances](https://github.com/NixOS/nixpkgs/issues/50105) of commit rights being taken from active committers.
Furthermore, [an RFC](https://github.com/NixOS/rfcs/blob/master/rfcs/0055-retired-committers.md) to periodically remove commit rights from inactive committers was accepted and [implemented](https://github.com/NixOS/nixpkgs/issues/88867).

This becomes much more tricky for more central permissions, such as GitHub org owners.
A success case was when it [was proposed to the foundation board](https://github.com/NixOS/foundation/issues/122) to remove @rbvermaa's as an org owner due to inactivity, who promptly replied with approval, which @zimbatm subsequently implemented.

### People with permissions are unresponsive

It can happen that somebody with permissions is asked to do something in PMs, but they don't respond.

### Multiple sources of truth

There is no central place where Nix organisation is documented.

## Detailed Design

Create the `NixOS/org` GitHub repository to be the source of truth for how Nix is organised, including:
- Official domain names like `nixos.org` and `nix.dev` and who controls them
- The configuration of the NixOS GitHub organisation, including its owners, repos, teams and who has what permissions
- Existing processes to nominate for permissions.
- Who, if any, is responsible and authoritative for the vision and goals of which part of the project.
- Who controls the official social media accounts such as YouTube, Mastodon and Twitter
- Legal status, such as the NixOS Foundation board and its members
- Policies such as the RFC process and where it stands in relation to any permissions
- The position of Nixpkgs committers and maintainers

Issues and pull requests will be open for anybody.
This gives us a central place to discuss Nix organisation and any propose changes to it.
Essentially crowd-sourcing organisation improvements, expansions and cleanups

Pull requests will be mergeable by the same people that could make those organisational changes currently.
After a pull request is merged, the changes must be implemented, with automation if possible, but manually otherwise.
Furthermore, in order for the repository to accurately reflect reality,
changes to the Nix organisation must not be done without going through this repository first.

Notably this won't immediately change the processes we have today,
they're only going to be made much more discoverable, explicit, transparent and declarative.

### Initialisation and migration

So far, organisation is spread among various people.
In order to make this work, everybody involved will have to agree with this proposal and use the repository for all organisational documentation and changes going forward.

Separate scratch space: https://pad.lassul.us/hw_qPVcuQgSkKvOTY1bWJw

## Examples

### Making a project official

If a group of people has been working on a project and think that it has become fit to become official,
they could open a pull request to add it as a resource, including
- The desired GitHub repository name
- If any, a domain name
- Themselves as owners

The proposal can then be discussed publicly, allowing people to express support/doubt or arguments for/against the proposal.

To create a new GitHub repository, the GitHub organisation owners approval is necessary,
while for the domain name, the infra teams approval is necessary.
Once those people have approved it, the pull request can be merged, and the changes will have to be implemented by the respective people.

This could be used for these popular but unofficial projects:
- The [Nix community GitHub organisation](https://github.com/nix-community/) and its projects, such as:
  - [Home-manager](https://github.com/nix-community/home-manager)
  - [nix-index](https://github.com/nix-community/nix-index)
- The [unofficial NixOS wiki](https://nixos.wiki/)
  - See also https://github.com/NixOS/foundation/issues/113
- Other repositories, such as
  - [flake-compat](https://github.com/edolstra/flake-compat)
  - [niv](https://github.com/nmattia/niv)

### Demoting a project from being official

If a project has not seen much activity for a while, somebody can create a pull request to remove the project.

After going through the proposal process, the Org team initiates the necessary change.
In this case this could mean asking the GitHub organisation owners to archive the projects repository, and asking the infrastructure team to create appropriate redirects.

### Joining a team

Initially, the process for joining a team would stay the same as it has been so far, and that would be documented in the repository.
However, a proposal can be made to change the process for joining a team to use the repository directly.
Such a proposal could be merged by the team lead.

Subsequent additions to the team could then be done with further pull requests to the repository.

### Changing the organisation proposal process

The process for how to accept changes to the organisation is encoded in the org repository itself.
Thus, any changes to it can be proposed with a pull request.

However, since there is no existing clear process for how to _decide_ over such policies, it would be unclear who could merge such a pull request.
So an RFC might still be needed for such substantial/controversial changes.

## Interactions



## Alternatives

A previous iteration of this proposal also attempted to create a policy for the responsibilities of resource owners, such as having to publish meeting notes, write reports, etc.
- (+) It would make sure that authority cannot be gained without responsibility
- (-) It's not necessary to have this in the initial version.
  We already have existing policies, even if they're underspecified and ad-hoc.
  Once a process to make organisational changes exist,
  a more concrete team responsibility policy can be proposed, along with how to enforce it.
- (-) This could stretch the discussions to the point where the proposal won't get implemented at all

A previous iteration of this proposal proposed having a predefined policy for teams, but also starting out with an empty organisation repository, with the hope that all resources and teams would be added to the repository over time, such that with each change, the relevant people would be informed of the team policy.
- (-) This only is beneficial if the team policy never changes, but it definitely will.
- (+) Starting out with an empty state gives a clear boundary between old processes and new ones
  - (-) If the "migration" to the new process fails, we'd be worse off in general

An alternative idea is keep the organisational source of truth as spread out as it is, but document it in a single place for transparency.
- (+) This is much easier to do socially, as it only requires that single place to be created and somebody to maintain it
- (-) This is likely to get outdated, even if people making organisational changes are asked to report updates
- (-) Doesn't allow the community to propose organisational changes.
  - If pull requests were allowed, it would have to be equivalent to the above proposal.

A previous iteration of this proposal was to also deprecate the RFC process.
- (-) It's not necessary to have this be part of this proposal.
- (-) The RFC process is so far still the only process to establish wider community consensus, so it's still needed.

A previous iteration of this proposal included the creation of a new Org team that would be in charge with handling PRs to the Org repository, with a community-driven RFC-like process for accepting proposals.
- (+) This would also make Nix organisation be more directly community controlled
- (-) This doesn't have to be part of this proposal, it's a big can of worms

Use `NixOS/.github` as the repository, which is where the GitHub organisations README can be declared
- (+) Would save one repository
- (-) Bad name, sounds (and is) GitHub specific

Make the repository issues/PRs limited to team members of some form
- (-) Doesn't work: If I'm only a contributing doc member and want to join the official docs team, I can't make a PR to add myself if the team is tracked there

## Future work

- As the organisational repo scales, it might become too resource intensive to manually implement the permission changes.
  Automation is not affordable quickly, but it should be improved as much as possible and necessary, making organisation as declarative as possible.
  
  This won't work for everything, but should work for at least GitHub.
  
  See also
  - https://github.com/NixOS/infra/issues/310
  - https://github.com/uwu-tools/peribolos
  - https://github.com/NixOS/infra/pull/360

## Unresolved questions

Nixpkgs internal organisation seems to work decently, despite ~200 people having full write permission.
Could this way of organisation work for the entire organisation? How or why not?
- It wouldn't work because everything in Nixpkgs is transparent, there's no way to change something without that being in the Git history (immutability). This is not the case for the entire Nix organisation.
- Furthermore, Nixpkgs and Nix is very functional/immutable itself
- Also consider: Nixpkgs is backed by Hydra, which only few people have write access to, but it's also a very stateful and non-transparent resource with more risk associated, unlike Git/Nix

How to handle commit access to this org repository?
- Anybody with permission to delegate permissions should be given write access.
  That's probably not a lot of people and they should be trusted.
- CODEOWNERS could be used to enforce that certain people need to approve PRs.
  Meta: Who's the CODEOWNER of CODEOWNER? Maybe the foundation board?
- This gets more risky in case such a repository is fully automated.
- Maybe best to leave this unaddressed for now, which is probably matching the current reality best.

## Drawbacks

There will be public fights about power structure, organisation, owners, etc.

## More related links

- https://github.com/NixOS/foundation/issues/71
- https://discourse.nixos.org/t/empowering-nix-teams-alpha-phase/22566
- https://discourse.nixos.org/t/where-did-you-get-stuck-in-the-nix-ecosystem-tell-me-your-story/31415
- https://discourse.nixos.org/t/nixcon-governance-workshop/32705
- https://discourse.nixos.org/t/nix-deserves-great-governance/26096
- https://discourse.nixos.org/t/what-do-you-think-of-teamification/34849
- https://discourse.nixos.org/t/decision-making-2-0-1-0-1/12851
