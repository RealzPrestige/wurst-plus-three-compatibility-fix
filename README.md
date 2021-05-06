# wurst-plus-three-compatibility-fix
Better compatibility for wurst-plus-three-0.4.0


Basically wurst-plus-three is incompatible with most clients. I made a fix for this, you can do this very easily yourself. Here is how you do it:

1. Get the wurst-plus-three source code.
2. Open intelij and import, run SetupDecompWorkspace.
3. Go to wurst-plus-three-0.4.0.zip\wurst-plus-three-0.4.0\src\main\java\me\travis\wurstplusthree\mixin\mixins\MixinMinecraft
4. Go to the far bottom until you find this line of code:

    @Redirect(method={"rightClickMouse"}, at=@At(value="INVOKE", target="Lnet/minecraft/client/multiplayer/PlayerControllerMP;getIsHittingBlock()Z", ordinal=0), require=1)
    private boolean isHittingBlockHook(PlayerControllerMP playerControllerMP) {
        return playerControllerMP.getIsHittingBlock();
    }
5. Change  , require=1) to , require=0) Here how its supposed to look after:

    @Redirect(method={"rightClickMouse"}, at=@At(value="INVOKE", target="Lnet/minecraft/client/multiplayer/PlayerControllerMP;getIsHittingBlock()Z", ordinal=0), require=0)
    private boolean isHittingBlockHook(PlayerControllerMP playerControllerMP) {
        return playerControllerMP.getIsHittingBlock();
    }

6. Build. 
