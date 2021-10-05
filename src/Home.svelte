<style>
    .picture {
        width:min(40vw,45vh);
        height:auto;
        left:calc(35vw - min(20vw, 22.5vh));
        position:relative;
        border: solid #292b2c .5vw;
        border-radius:50%;
        box-shadow: 0px -5px 2vw .1vw #292b2c;
    }
    .top-text {
        height:6vw;
        left:30vw;
        width:40vw;
        position:relative;
        font-size:5vw;
        text-align:center;
    }
    .picture-surround {
        border-left: solid #292b2c .5vw;
        border-right: solid #292b2c .5vw;
        width:70vw;
        left:15vw;
        position:relative;
        border-radius:5vw;
    }
    .tag-text {
        position:relative; 
        text-align:center;
        width:50vw; 
        left:25vw; 
        font-size:3.3vw;
        text-decoration:underline;
        text-decoration-color: goldenrod;
        text-decoration-thickness: .2vw;
    }
    .home-container > :last-child {
    margin-bottom: 3em;
}
</style>
<div class="home-container" style="position:relative;top:100px;left:0">
    <div style="text-align:center;position:relative;margin:auto;width:100vw;">
        <h1 class=top-text>
            Lane Lewis
        </h1>
    </div>
    <div class=picture-surround>
        <img src = "./images/Portrait.jpeg" alt="responsive" class=picture/>
    </div>
    <div style="position:relative;">
        <h1 class=tag-text>
            Machine Learning, Neuroscience, and Mathematics Enthusiast
        </h1>
    </div>
    <div style="display:flex;flex-direction:row;justify-content:space-evenly;position:relative">
        <div style="width:43vw;">
            <h1 style="text-align:center;border-bottom: solid #292b2c">About</h1>
            <div class=bottom-container style="width:40vw;position:relative;left:2vw">
                My interests lie in using neuroscience to inform the development of intelligent algorithms,
                and using intelligent algorithms to accelerate neuroscience research. I also have a general
                interest in machine learning algorithm development and building software
                that can automate, predict, and fluidly conform to human behaviors. A jack of all trades,
                I have a background in mathematical analysis and proofs, both web and scientific computing,
                machine learning, and neuroscience. 
            </div>
        </div>
        <div style = "width:43vw">
            <h1 style="text-align:center;border-bottom: solid #292b2c">Information</h1> 
            <div class=bottom-container style="width:40vw;position:relative;left:1.5vw">
                <h3 style="text-align:center;height:5px">
                    Documents
                </h3>
                <div style="display:flex;flex-direction:row;justify-content:center;height:10px">
                    <div style="width:22vw;text-align:center">
                        <a href=./documents/resume.pdf>Resume</a> 
                    </div>
                    <div style="width:22vw;text-align:center">
                        <a href=./documents/CV.pdf>CV</a>
                    </div>
                    <div style="width:22vw;text-align:center">
                        <a href=./documents/Transcript.pdf>Transcript</a>
                    </div>
                </div>
                <h3 style="text-align:center;height:5px">
                   Contact
                </h3>            
                <div style="text-align:center">
                    Email: lanerobertlewis@email.arizona.edu
                    <br>
                    Phone: (406) 830-4470
                </div>
            </div>
        </div>
    </div>
</div>
<div style="position:relative;height:100px"></div>